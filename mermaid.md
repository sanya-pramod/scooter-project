classDiagram
    class ScooterApp {
        +stations : object
        +registeredUsers : object
        +registerUser(username, password, age)
        +loginUser(username, password)
        +logoutUser(username)
        +createScooter(station)
        +dockScooter(scooter, station)
        +rentScooter(scooter, user)
        +print()
    }
    
    class Scooter {
        +station : string
        +user : User
        +serial : number
        +charge : number
        +isBroken : boolean
        +rent(user : User)
        +dock(station : string)
    }

    class User {
        +username : string
        +password : string
        +age : number
        +loggedIn : boolean
        +login(password : string)
        +logout()
    }

    ScooterApp "1" --> "0..*" Scooter : manages
    ScooterApp "1" --> "0..*" User : manages
    Scooter "0..1" --> "1" User : rents
    Scooter "0..1" --> "1" ScooterApp : belongs to
    User "0..*" --> "0..*" Scooter : rents
