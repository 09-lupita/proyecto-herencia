#include <iostream>
#include <string>
using namespace std;

// clase 
class ProductoOptico {
protected:
    string tipo;
    string marca;
    float precio;
public:
    void setProducto(string t, string m, float p) {
        tipo = t;
        marca = m;
        precio = p;
    }

    void mostrarProducto() {
        cout << "Marca de lentes de contacto: " << marca << endl;
        cout << "Precio: $" << precio << endl;
    }

    float getPrecio() {
        return precio;
    }
};

// Clase 
class Cliente {
protected:
    string nombre;
    string telefono;
public:
    void setCliente(string n, string t) {
        nombre = n;
        telefono = t;
    }

    void mostrarCliente() {
        cout << "Nombre del paciente: " << nombre << endl;
        cout << "Teléfono: " << telefono << endl;
    }
};

// Clase 
class Diagnostico {
protected:
    string problemaVisual;
    string od;
    string oi;
public:
    void setDiagnostico(string problema, string od_val, string oi_val) {
        problemaVisual = problema;
        od = od_val;
        oi = oi_val;
    }

    void mostrarDiagnostico() {
        cout << "Diagnóstico: " << problemaVisual << endl;
        cout << "OD: " << od << endl;
        cout << "OI: " << oi << endl;
    }
};

// Clase derivada:
class Venta : public ProductoOptico, public Cliente, public Diagnostico {
private:
    int cantidad;
public:
    void setVenta(string n, string tlf, string problema, string od_val, string oi_val,
                  string tipoProd, string marcaProd, float precioProd, int cant) {
        setCliente(n, tlf);
        setDiagnostico(problema, od_val, oi_val);
        setProducto(tipoProd, marcaProd, precioProd);
        cantidad = cant;
    }

    void mostrarVenta() {
        cout << "=== NOTA DE VENTA ===" << endl;
        mostrarCliente();
        mostrarDiagnostico();
        mostrarProducto();
        cout << "Cantidad de lentes de contacto: " << cantidad << endl;
        cout << "Total a pagar: $" << getPrecio() * cantidad << endl;
        cout << "Gracias por visitarnos" << endl;
    }
};

int main() {
    Venta venta1;
    venta1.setVenta(
        "Norma Hernández Zarate",
        "5625170908",
        "Miopía y astigmatismo",
        "-1.25 -1.00 x120",
        "-0.50 -2.00 x0",
        "Lentes de contacto",
        "Biofinity",
        580.0,
        2 // Cantidad de lentes
    );

    venta1.mostrarVenta();

    return 0;
}
