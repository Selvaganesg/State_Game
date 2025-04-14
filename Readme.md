# State Game


## PROGRAM:
```
import turtle
import pandas

screen = turtle.Screen()
screen.setup(width=800,height=800)
image = "india.gif"
screen.addshape(image)
turtle.shape(image)

data = pandas.read_csv("india_29_state- Sheet1.csv")
india_states = data.State.to_list()
find_state = []

while len(india_states)<50:

    user_state = screen.textinput(title="Guess the State",prompt=f"{len(find_state)}/29 What the next state name").title()
    
    if user_state in india_states:
        find_state.append(user_state)
        state_data = data[data.State == user_state]
        tom = turtle.Turtle()
        tom.hideturtle()
        tom.penup()
        tom.goto(state_data.x.item(),state_data.y.item())
        tom.write(user_state)

    if user_state=="Exit":
        missing_state = [state for state in india_states if state not in find_state]
        df = pandas.DataFrame(missing_state)
        df.to_csv("Not_Find_State.csv")
        print(df)
        break
```

## OUTPUT:
