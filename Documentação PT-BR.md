# Orion Library
Esta documentação é para a versão estável da Orion Library.

## Inicializando a biblioteca
```lua
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
```



## Criando uma janela
```lua
local Window = OrionLib:MakeWindow({Name = "Title of the library", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

--[[
Name = <string> - The name of the UI.
HidePremium = <bool> - Whether or not the user details shows Premium status or not.
SaveConfig = <bool> - Toggles the config saving in the UI.
ConfigFolder = <string> - The name of the folder where the configs are saved.
IntroEnabled = <bool> - Whether or not to show the intro animation.
IntroText = <string> - Text to show in the intro animation.
IntroIcon = <string> - URL to the image you want to use in the intro animation.
Icon = <string> - URL to the image you want displayed on the window.
CloseCallback = <function> - Function to execute when the window is closed.
]]
```



## Criando uma guia
```lua
local Tab = Window:MakeTab({
	Name = "Tab 1",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - The name of the tab.
Icon = <string> - The icon of the tab.
PremiumOnly = <bool> - Makes the tab accessible to Sirus Premium users only.
]]
```
## Criando uma seção
```lua
local Section = Tab:AddSection({
	Name = "Section"
})

--[[
Name = <string> - The name of the section.
]]
```
Você pode adicionar elementos às seções da mesma forma que normalmente os adicionaria a uma guia.

## Notificando o usuário
```lua
OrionLib:MakeNotification({
	Name = "Title!",
	Content = "Notification content... what will it say??",
	Image = "rbxassetid://4483345998",
	Time = 5
})

--[[
Title = <string> - The title of the notification.
Content = <string> - The content of the notification.
Image = <string> - The icon of the notification.
Time = <number> - The duration of the notfication.
]]
```



## Criando um botão
```lua
Tab:AddButton({
	Name = "Button!",
	Callback = function()
      		print("button pressed")
  	end    
})

--[[
Name = <string> - The name of the button.
Callback = <function> - The function of the button.
]]
```


## Criando uma alternância de caixa de seleção
```lua
Tab:AddToggle({
	Name = "This is a toggle!",
	Default = false,
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the toggle.
Default = <bool> - The default value of the toggle.
Callback = <function> - The function of the toggle.
]]
```

### Alterando o valor de um Toggle existente
```lua
CoolToggle:Set(true)
```



## Criando um seletor de cores
```lua
Tab:AddColorpicker({
	Name = "Colorpicker",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the colorpicker.
Default = <color3> - The default value of the colorpicker.
Callback = <function> - The function of the colorpicker.
]]
```

### Configurando o valor do seletor de cores
```lua
ColorPicker:Set(Color3.fromRGB(255,255,255))
```


## Criando um controle deslizante
```lua
Tab:AddSlider({
	Name = "Slider",
	Min = 0,
	Max = 20,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "bananas",
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the slider.
Min = <number> - The minimal value of the slider.
Max = <number> - The maxium value of the slider.
Increment = <number> - How much the slider will change value when dragging.
Default = <number> - The default value of the slider.
ValueName = <string> - The text after the value number.
Callback = <function> - The function of the slider.
]]
```

### Alterar valor do controle deslizante
```lua
Slider:Set(2)
```
Certifique-se de tornar seu controle deslizante uma variável (local CoolSlider = Tab:AddSlider...) para que isso funcione.


## Criando um rótulo
```lua
Tab:AddLabel("Label")
```

### Alterando o valor de um rótulo existente
```lua
CoolLabel:Set("Label New!")
```


## Criando um parágrafo
```lua
Tab:AddParagraph("Paragraph","Paragraph Content")
```

### Alterando um parágrafo existente
```lua
CoolParagraph:Set("Paragraph New!", "New Paragraph Content!")
```


## Criando uma entrada adaptativa
```lua
Tab:AddTextbox({
	Name = "Textbox",
	Default = "default box input",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - The name of the textbox.
Default = <string> - The default value of the textbox.
TextDisappear = <bool> - Makes the text disappear in the textbox after losing focus.
Callback = <function> - The function of the textbox.
]]
```


## Criando um atalho de teclado
```lua
Tab:AddBind({
	Name = "Bind",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end    
})

--[[
Name = <string> - The name of the bind.
Default = <keycode> - The default value of the bind.
Hold = <bool> - Makes the bind work like: Holding the key > The bind returns true, Not holding the key > Bind returns false.
Callback = <function> - The function of the bind.
]]
```

### Alterando o valor de um vínculo
```lua
Bind:Set(Enum.KeyCode.E)
```


## Criando um menu suspenso
```lua
Tab:AddDropdown({
	Name = "Dropdown",
	Default = "1",
	Options = {"1", "2"},
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - The name of the dropdown.
Default = <string> - The default value of the dropdown.
Options = <table> - The options in the dropdown.
Callback = <function> - The function of the dropdown.
]]
```

### Adicionando um conjunto de novos botões suspensos a um menu existente
```lua
Dropdown:Refresh(List<table>,true)
```

O valor boolean "true" acima indica se os botões atuais serão excluídos ou não.
### Selecionando uma opção suspensa
```lua
Dropdown:Set("dropdown option")
```

# Concluindo seu script (OBRIGATÓRIO)
A função abaixo precisa ser adicionada no final do seu código.
```lua
OrionLib:Init()
```

### Como funcionam os sinalizadores.
O recurso de sinalizadores na interface do usuário pode ser confuso para algumas pessoas. Ele tem o propósito de ser o ID de um elemento no arquivo de configuração e possibilita o acesso ao valor de um elemento em qualquer lugar do código.
Abaixo está um exemplo de uso de sinalizadores.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Os sinalizadores funcionam apenas com alternância, controle deslizante, menu suspenso, vinculação e seletor de cores.

### Fazendo sua interface funcionar com configurações.
Para fazer sua interface usar a função configs você primeiro precisa adicionar os argumentos `SaveConfig` e `ConfigFolder` à sua função de janela. A explicação desses argumentos acima.
Então você precisa adicionar os valores `Flag` e `Save` a cada alternância, controle deslizante, menu suspenso, ligação e seletor de cores que deseja incluir no arquivo de configuração.
O argumento `Flag = <string>` é o ID de um elemento no arquivo de configuração.
O argumento `Save = <bool>` inclui o elemento no arquivo de configuração.
Os arquivos de configuração são criados para cada jogo em que a biblioteca é iniciada.

## Destruindo a Interface
```lua
OrionLib:Destroy()
```
