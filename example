import pygame as py
py.init()
font_name = py.font.match_font('Arial') #поиск шрифта
size = 18 #его размер

w = 1200
h = 800
win = py.display.set_mode((w,h))

bg = py.image.load('replace.png') #загрузка (добавление) картинки
bg = py.transform.scale(bg, (w,h)) #изменение картинки на полный экран

stbg = py.image.load('darkbg.jpg')
stbg = py.transform.scale(stbg, (w,h))

#plr = py.image.load('devka.png')
#plr = py.transform.scale(plr, (32, 32))

x = w//2
y = h//2

class Player(py.sprite.Sprite): #все, что связано с игроком
  def __init__(self, plr_x, plr_y): #используется для появления игрока
    py.sprite.Sprite.__init__(self)
    self.plr_x = plr_x
    self.plr_y = plr_y
    self.speed_x = 1
    self.speed_y = 0
    self.image = py.image.load("devka.png")
    self.rect = self.image.get_rect()
    self.rect.centerx = self.plr_x
    self.rect.bottom = self.plr_y
  def update(self):
    self.rect.x += self.speed_x
    self.rect.y += self.speed_y
    key = py.key.get_pressed()
    if key[py.K_UP]:
      self.speed_y = -1
    if key[py.K_DOWN]:
      self.speed_y = 1
  def move(self): #отвечает за передвижение игрока (пока что не работает)
    if self.plr_turn:
      self.plr_x -= 2
    else:
      self.plr_x += 2
    if self.plr_x >= 560:
      self.plr_turn = True
    elif self.plr_x <= 40:
      self.plr_turn = False
all_sprites = py.sprite.Group()
player = Player(w//2,h//2)
all_sprites.add(player)

#вступительный экран
name = ''
def draw_text(surf, text, x, y, size=size, color=(255,255,255)):
  font = py.font.Font(font_name, size) #определение шрифта
  text_surface = font.render(text, True, color)
  text_rect = text_surface.get_rect()
  text_rect.midtop = (x,y)
  surf.blit(text_surface, text_rect)
def user_name(surf,text,x,y,size):
  font = py.font.Font(font_name, size) #определение шрифта
  text_surface = font.render(text, True, color=(255,255,255))
  text_rect = text_surface.get_rect()
  text_rect.midtop = (x, y)
  surf.blit(text_surface, text_rect)
fps = py.time.Clock
main = True
while main:
  for event in py.event.get():
    if event.type == py.QUIT:
      exit()
    elif event.type == py.KEYDOWN:
      if event.key == py.K_BACKSPACE:
        name = name[:-1]
      elif event.key == py.K_RETURN:
        main = False
      else:
        name += event.unicode
  win.fill((0,0,0))
  win.blit(bg, (0, 0)) #добавление картинки в игру

  draw_text(win, 'Введите имя:', (w//2),(h//2))
  draw_text(win, name, 300,325)
  py.display.update()
  py.time.delay(16) #примерно 60 фпс

#сама игра
while True:
  for i in py.event.get():
    if i.type == py.QUIT:
      exit()
  win.blit(stbg, (0,0))
  all_sprites.update()
  all_sprites.draw(win)
  #player = Player(plr, w//2, (h-50), False)
  #win.blit(player.plr, (player.plr_x, player.plr_y))
  #player.move()

  py.display.update()
  py.time.delay(16)
