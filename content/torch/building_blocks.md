# Building block to create a NN: Module, Sequential, ModuleList, ModuleList



All modules are involved in `torch.nn`

## 1. Module: the main building block 
**it defines the base class for all neural network and you must subclass it**. 

## 2. Sequential: stack and merge layer
It is a easy way to create a network. We can stack layers into a Sequential, as long as the output of previous layer is equal to the input of the next and use it as a nn 

### 2.1. Dynamic Sequential: create multiple layers at once


## 3. ModuleList: when we need to iterate
ModuleList allows you to store modules in a list. But the inner layers are not connected because it don't have forward method. If we want to use it, you should iterate through inner layers. It's advantages over Sequential is that you can get the output of each inner layers if you want when iterate them (example when you build U net) 

```python
class MyModule(nn.Module):
    def __init__(self, sizes):
        super().__init__()
        self.layers = nn.ModuleList([nn.Linear(in_f, out_f) for in_f, out_f in zip(sizes, sizes[1:])])
        self.trace = []
        
    def forward(self,x):
        for layer in self.layers:
            x = layer(x)
            self.trace.append(x)
        return x
```

## 4. ModuleDict: when we need to choose


## 5. Summary.

1. Use Module when you have a big block compose of multiple smaller blocks
2. Use Sequential when you want to create a small block from layers
3. Use ModuleList when you need to iterate through some layers or building blocks and do something
4. Use ModuleDict when you need to parametise some blocks of your model, for example an activation function

That's all folks!


## Reference
1. [source](https://gist.github.com/FrancescoSaverioZuppichini/7b228760eefe8e77fb0a37b5783a379c)