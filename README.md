# E08b-Adding-Tiles

I continued working from the last assignment, E08a-Paddle Ball. On Cavas, there was a repository for the second part of the assignment. I forked and cloned the given repository on Canvas. I opened the file on Godot. For this assignment, I added another node representing node and child nodes representing the tiles in different colors, such as gray and red. I also added some tiles with different colors in 5 rows. While I was working on adding the tiles, I used the following code: 
var gray = preload("res://Assets/tile_gray.png")
var red = preload("res://Assets/tile_red.png")
var blue = preload("res://Assets/tile_blue.png")
var green = preload("res://Assets/tile_green.png")
var purple = preload("res://Assets/tile_purple.png")

onready var sprite = get_node("Sprite")
var score = 10

func _ready():
   if get_parent().name == "Gray Tiles":
       sprite.set_texture(gray)
   if get_parent().name == "Red Tiles":
       sprite.set_texture(red)
       score = 20
   if get_parent().name == "Blue Tiles":
       sprite.set_texture(blue)
       score = 30
   if get_parent().name == "Green Tiles":
       sprite.set_texture(green)
       score = 40
   if get_parent().name == "Purple Tiles":
       sprite.set_texture(purple)
       score = 50

I added another code for the ball so the ball can break the tiles. The code I used for the ball was: 

func _ready():
    contact_monitor = true
    set_max_contacts_reported(4)

func _physics_process(delta):
    var bodies = get_colliding_bodies()
    for body in bodies:
        if body.is_in_group("Tiles"):
            body.queue_free()
    
    if position.y > get_viewport_rect().end.y:
        queue_free()
        print("Died")
           
When I added code for both tiles and balls, I ran the game to see if it works properly. Luckily, it worked well. Everytime when the player bounces the ball off the paddle by using a mouse, the ball will crack the tiles. The tiles will disappear when they get hit. After running the game, I commited to GitHub by using GitHub Desktop. Then, I edited LICENSE and README.md.
