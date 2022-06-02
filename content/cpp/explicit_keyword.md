there are two keyword for creating a contructor: explicit, implicit. Default, a contructor is created by using keyword implicit.

implicit means that the compiler is allowed to make one implicit conversion to resolve the parameter to a function. Or you can use contructors callable with a single parameter to convert from one type to another in order to get the right type for parameter.
Example:
'''
class Foo
{
    private:
    int m_foo;

    public:
    Foo (int foo): m_foo(foo){}
    int getFoo(){return m_foo;}
};

void DoBar (Foo foo){
    int i = goo.getFoo();
}

void main(){
    DoBar(42); // <-- you can cast an int arg to Foo arg 
}
'''

The argument is not a Foo object, but an int. However, there is a contructor for Foo that take an int argument, so this contrunctor can be used to convert the paramter to the correct type.

The compiler is allowed to do this once for each parameter.

The keyword explicit will prevent the compiler from using implicit conversions. You have to give the right argument type for the function.

'''
void main(){
    DoBar(Foo(42)); // <-- you can cast an int arg to Foo arg 
}
'''