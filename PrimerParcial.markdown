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


+ Creamamos nuestra clase Lista simple

```c++
class ListaSimple{
public:
    ListaSimple(){
    //Tendra atributos que haran referencia al primer y ultio nodo
        primero=0;
        ultimo=0;
     //Este size nos permitira saber la longitud de nuestra lista 
        size=0;
    }
        int getTamanio(){return size;}
    }

```


+ Metodo insertar en una lista simple
```c++
class    void insertar(string palabra,string remplazo){
        NodoS *n = new NodoS(palabra,remplazo); //Reservamos el nuevo nodo en memoria
        //Primero verificamos si la lista esta vacia
        if(this->estaVacia()){
            this->primero=n; //primero sera el nuevo nodo
            this->ultimo =n; // utlimo sera el nuevo nodo
            //esto porque es el primer nodo de la lista
            this->size++;
        }else{
          //Decimos que si no, el apuntador siguiente del ulitmo nodo ahora apuntara al nuevo nodo 
            this->ultimo->setSiguiente(n); 
            this->ultimo=n;  // ultimo sera ahora el nuevo nodo, esto porque agregamos al final de la lista
            this->size++;
        }
    }

```






