## TDA
Tipos de datos creados por el programador, que deben ser opacos (accesibilidad)

+ Create a list by starting a line with `+`, `-`, or `*`

+ Tipos de datos 
  + Enteros,reales,booleanos,caracteres
Enumerados,arreglos
Son Opacos


## Listas

+ Lista Simple 
es aquella que el apuntador unicamente va hacia siguiente 

+ Creamos nuestra clase nodo

```c++
class Nodo{
public:
    NodoS(string palabra_,string remplazar_){
        siguiente=0;  //Solo tendra un apuntador a siguiente
        palabra = palabra_;
        remplazar=remplazar_;
    }
    
    Nodo *getSiguiente(){return siguiente;}
    
    void setSiguiente(NodoS *n){siguiente=n;}
    
    string getPalabra(){return palabra;}
    
    string getRemplazar(){return remplazar;}

    void setPalabra(string palabra_){
        palabra = palabra_;
    }
    void setRemplazar(string remplazar_){
        palabra = remplazar_;
    }


private:
    Nodo* siguiente;
    //En este ejemplo tendremos que el nodo tendra dos atributos de tipo string
    string palabra;  
    string remplazar;
};

```



