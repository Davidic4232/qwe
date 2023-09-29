class GeneratorContainer:
    def __init__(self, generator_function):
        self.generator_function = generator_function

    def __iter__(self):
        return self

    def __next__(self):
        return next(self.generator_function)


def my_generator():
    yield 1
    yield 2
    yield 3
    
container = GeneratorContainer(my_generator())


for value in container:
    print(value)



    

def safe_calculate(func):
    def wrapper(expression):
        
       
try:
            result = eval(expression)
            return result
        
       
except Exception as e:
            return f"Error: {e}"
    
    return wrapper

@safe_calculate
def calculate(expression):
    return expression


print(calculate("2 + 2"))  
print(calculate("5 / 0")) 

