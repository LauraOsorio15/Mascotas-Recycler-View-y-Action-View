# Mascotas-Recycler-View-y-Action-View
# Definir la entidad "Mascota":
public class Mascota {
    private String nombre;
    private int rating;

    public Mascota(String nombre, int rating) {
        this.nombre = nombre;
        this.rating = rating;
    }

    public String getNombre() {
        return nombre;
    }

    public int getRating() {
        return rating;
    }
}
#Crear el diseño de cada elemento de la lista
<!-- item_mascota.xml -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:orientation="horizontal"
    android:padding="16dp">

    <TextView
        android:id="@+id/textViewNombre"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1"
        android:textSize="18sp"
        android:textStyle="bold"/>

    <ImageView
        android:id="@+id/imageViewRating"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/ic_bone_gray"
        android:layout_marginStart="8dp"/>
</LinearLayout>

#Definir los íconos de huesos
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    android:width="24dp"
    android:height="24dp"
    android:viewportWidth="24"
    android:viewportHeight="24"
    android:tint="?attr/colorControlNormal">
    <path
        android:fillColor="@android:color/darker_gray"
        android:pathData="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
</vector>

<vector xmlns:android="http://schemas.android.com/apk/res/android"
    android:width="24dp"
    android:height="24dp"
    android:viewportWidth="24"
    android:viewportHeight="24"
    android:tint="?attr/colorControlNormal">
    <path
        android:fillColor="@android:color/holo_orange_light"
        android:pathData="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
</vector>

#Usar el RecyclerView en tu actividad principal
import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;
import androidx.recyclerview.widget.LinearLayoutManager;
import androidx.recyclerview.widget.RecyclerView;

import java.util.ArrayList;
import java.util.List;

public class MainActivity extends AppCompatActivity {

    private RecyclerView recyclerView;
    private MascotaAdapter mascotaAdapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        recyclerView = findViewById(R.id.recyclerView);
        recyclerView.setLayoutManager(new LinearLayoutManager(this));

        List<Mascota> mascotas = obtenerMascotas();
        mascotaAdapter = new MascotaAdapter(mascotas, this);
        recyclerView.setAdapter(mascotaAdapter);
    }

    private List<Mascota> obtenerMascotas() {
        List<Mascota> mascotas = new ArrayList<>();
        mascotas.add(new Mascota("Max", 3));
        mascotas.add(new Mascota("Bella", 5));
        // Agrega más mascotas según sea necesario
        return mascotas;
    }
}
