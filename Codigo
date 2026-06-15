1. Model – Tarefa.kt
package com.example.smarttask.model

data class Tarefa(
    var titulo: String,
    var concluida: Boolean = false
)
2. Adapter – TarefaAdapter.kt
package com.example.smarttask.adapter

import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.Button
import android.widget.CheckBox
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView
import com.example.smarttask.R
import com.example.smarttask.model.Tarefa

class TarefaAdapter(
    private val lista: MutableList<Tarefa>,
    private val onDelete: (Int) -> Unit,
    private val onEdit: (Int) -> Unit
) : RecyclerView.Adapter<TarefaAdapter.TarefaViewHolder>() {

    class TarefaViewHolder(view: View) : RecyclerView.ViewHolder(view) {
        val titulo = view.findViewById<TextView>(R.id.textTitulo)
        val check = view.findViewById<CheckBox>(R.id.checkConcluida)
        val excluir = view.findViewById<Button>(R.id.btnExcluir)
        val editar = view.findViewById<Button>(R.id.btnEditar)
    }

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): TarefaViewHolder {
        val view = LayoutInflater.from(parent.context)
            .inflate(R.layout.item_tarefa, parent, false)
        return TarefaViewHolder(view)
    }

    override fun getItemCount() = lista.size

    override fun onBindViewHolder(holder: TarefaViewHolder, position: Int) {
        val tarefa = lista[position]
        holder.titulo.text = tarefa.titulo
        holder.check.isChecked = tarefa.concluida

        holder.check.setOnCheckedChangeListener { _, isChecked ->
            tarefa.concluida = isChecked
        }

        holder.excluir.setOnClickListener { onDelete(position) }
        holder.editar.setOnClickListener { onEdit(position) }
    }
}
3. Utils – Prefs.kt
package com.example.smarttask.utils

import android.content.Context
import com.example.smarttask.model.Tarefa
import com.google.gson.Gson
import com.google.gson.reflect.TypeToken

class Prefs(context: Context) {

    private val prefs = context.getSharedPreferences("tarefas", Context.MODE_PRIVATE)

    fun salvar(lista: MutableList<Tarefa>) {
        val json = Gson().toJson(lista)
        prefs.edit().putString("lista", json).apply()
    }

    fun carregar(): MutableList<Tarefa> {
        val json = prefs.getString("lista", null)
        return if (json != null) {
            val tipo = object : TypeToken<MutableList<Tarefa>>() {}.type
            Gson().fromJson(json, tipo)
        } else {
            mutableListOf()
        }
    }
}
4. Activities – MainActivity.kt
package com.example.smarttask.activities

import android.app.AlertDialog
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView
import com.example.smarttask.R
import com.example.smarttask.adapter.TarefaAdapter
import com.example.smarttask.model.Tarefa
import com.example.smarttask.utils.Prefs

class MainActivity : AppCompatActivity() {

    private lateinit var recycler: RecyclerView
    private lateinit var editTarefa: EditText
    private lateinit var btnAdicionar: Button
    private lateinit var adapter: TarefaAdapter
    private lateinit var prefs: Prefs
    private var lista = mutableListOf<Tarefa>()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)

        recycler = findViewById(R.id.recyclerTarefas)
        editTarefa = findViewById(R.id.editTarefa)
        btnAdicionar = findViewById(R.id.btnAdicionar)
        prefs = Prefs(this)
        lista = prefs.carregar()

        adapter = TarefaAdapter(
            lista,
            onDelete = { position ->
                lista.removeAt(position)
                prefs.salvar(lista)
                adapter.notifyDataSetChanged()
            },
            onEdit = { position ->
                val editText = EditText(this)
                editText.setText(lista[position].titulo)
                AlertDialog.Builder(this)
                    .setTitle("Editar Tarefa")
                    .setView(editText)
                    .setPositiveButton("Salvar") { _, _ ->
                        val novoTexto = editText.text.toString().trim()
                        if (novoTexto.isNotEmpty()) {
                            lista[position].titulo = novoTexto
                            prefs.salvar(lista)
                            adapter.notifyItemChanged(position)
                        }
                    }
                    .setNegativeButton("Cancelar", null)
                    .show()
            }
        )

        recycler.layoutManager = LinearLayoutManager(this)
        recycler.adapter = adapter

        btnAdicionar.setOnClickListener {
            val texto = editTarefa.text.toString().trim()
            if (texto.isNotEmpty()) {
                lista.add(Tarefa(texto))
                prefs.salvar(lista)
                adapter.notifyItemInserted(lista.size - 1)
                editTarefa.text.clear()
            }
        }
    }
}
5. Layout – activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="SmartTask Secure"
        android:textSize="28sp"
        android:textStyle="bold"
        android:layout_marginBottom="16dp"/>

    <EditText
        android:id="@+id/editTarefa"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Digite uma tarefa"
        android:inputType="text"/>

    <Button
        android:id="@+id/btnAdicionar"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Adicionar Tarefa"
        android:layout_marginTop="8dp"/>

    <androidx.recyclerview.widget.RecyclerView
        android:id="@+id/recyclerTarefas"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_marginTop="16dp"/>
</LinearLayout>
6. Layout – item_tarefa.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:padding="12dp">

    <CheckBox
        android:id="@+id/checkConcluida"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <TextView
        android:id="@+id/textTitulo"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:textSize="18sp"/>

    <Button
        android:id="@+id/btnEditar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Editar"/>

    <Button
        android:id="@+id/btnExcluir"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Excluir"/>
</LinearLayout>
