
## Table of Contents
1. [Register](#register)

   1.1. [Category](#category)

   1.2. [Properties](#properties)

2. [Creature](#creature)

   2.1. [UIcreature](#uicreature)

   2.2. [Creature](#creature2)

3. [Widget](#widget)

   2.1. [Tile Widget](#widgettile)

   2.2. [Creature Widget](#widgetcreature)


4. [Particle](#Particle)
5. [Server Connection](#connection)


***
## <a name="register"> 1.- Register</a>

https://github.com/mehah/otclient/blob/main/modules/game_attachedeffects/effects.lua


### <a name="category"> 1.1 Category</a>
**ThingCategoryEffect**: 

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/ThingCategoryEffect.png?raw=true" > 



**ThingCategoryCreature** : 

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/ThingCategoryCreature.png?raw=true" > 


**ThingExternalTexture**: are images in Png | Apng https://github.com/mehah/otclient/tree/main/data/images/game/effects


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/ThingExternalTexture.png?raw=true" > 

```lua
--[[`
    register(id, name, thingId, thingType, config)
    config = {
        speed, disableWalkAnimation, shader, drawOnUI, opacity
        duration, loop, transform, hideOwner, size{width, height}
        offset{x, y, onTop}, dirOffset[dir]{x, y, onTop},
        light { color, intensity}, drawOrder(only for tiles),
        bounce{minHeight, height, speed},
        pulse{minHeight, height, speed},
        fade{start, end, speed}

        onAttach, onDetach
    }
`]]
```
--

### <a name="properties"> 1.2 Properties</a>
_speed_:

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_speed_.gif?raw=true" > 


_fade_:

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/fade_1.gif?raw=true" > 

_pulse_:

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/pulsework_1.gif?raw=true" > 



_disableWalkAnimation_


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_disableWalkAnimation_.gif?raw=true" > 

_shader_


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_shader_.gif?raw=true" > 

_opacity_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_opacity_.gif?raw=true" > 


_duration_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/duration.gif?raw=true" > 

_transform_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_transform_.gif?raw=true" > 



_loop_

`coming soon`

_hideOwner_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_hideOwner_.gif?raw=true" > 


_size_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_size_.gif?raw=true" > 





_offset_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/offset_1.gif?raw=true" > 

_dirOffset_ (offset depends on the direction of the character)

- horizontal

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/horizontal.gif?raw=true" > 



- vertical

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/vertical.gif?raw=true" > 

_front/back_:

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/aebolean.gif?raw=true" > 

_bounce_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/bones.gif?raw=true" > 


# <a name="creature"> 2.- Creature</a>

###   <a name="uicreature">    - 2.1. UIcreature:</a>
 

```lua
  UICreature
    id: creature
    anchors.top: XXXXX.top
    anchors.left: XXXXX.left
    anchors.bottom: XXXXX.bottom
    size: 32 32 
```

```lua
UICreature:getCreature():attachEffect(g_attachedEffects.getById(ID))
```


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/UIcreature.png?raw=true" > 

###   <a name="creature2">    - 2.2. Creature:</a>

```lua
local creature = g_map.getCreatureById(Creature_ID)
if creature  then
     creature:attachEffect(g_attachedEffects.getById(ID))
end
```
**or**

```lua
 g_game.getLocalPlayer():attachEffect(g_attachedEffects.getById(ID))
```
<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/bones.gif?raw=true" > 

# <a name="widget"> 3.- Widget</a>

###   <a name="widgettile">    - 3.1. Tile Widget:</a>
```lua
local tile = g_map.getTile(g_game.getLocalPlayer():getPosition())
local widget = g_ui.createWidget('Panel')
widget:setSize({width = 90,height = 22})
widget:setText("OTC Redemption")
widget:setFont("terminus-10px")
widget:setBackgroundColor('#111111cc')
widget:setMarginBottom(40)
tile:attachWidget(widget)
```

![image](https://raw.githubusercontent.com/kokekanon/OTredemption-Picture-NODELETE/main/Picture/Attached%20Effect/Tile/002_widget.png?raw=true)


###   <a name="widgetcreature">    - 3.2. Creature Widget:</a>
```lua
local widget = g_ui.createWidget('Panel')
widget:setTextAutoResize(true)
widget:setText("Yes you can Deux!!! ;)")
widget:setFont("terminus-10px")
widget:setBackgroundColor('red')
widget:setColor('black')
widget:setMarginBottom(40)
widget:setFontScale(3)
g_game.getLocalPlayer():attachWidget(widget)
```


# <a name="Particle"> 4.- Particle</a>

###   <a name="particlecreature">    - 4.1. Creature Widget:</a>
```lua
g_game.getLocalPlayer():attachParticleEffect("creature-effect")
```
![image](https://github.com/kokekanon/OTredemption-Picture-NODELETE/raw/main/Picture/Attached%20Effect/Creature/003_particula.gif?raw=true)

###   <a name="particletile">    - 4.2. Tile Widget:</a>
```lua
g_map.getTile(g_game.getLocalPlayer():getPosition()):attachParticleEffect("creature-effect")
```
![image](https://github.com/kokekanon/OTredemption-Picture-NODELETE/raw/main/Picture/Attached%20Effect/Tile/003_particulas.gif?raw=true)

# <a name="connection"> 5.- Server Connection</a>
##   - 5.1. TFS  : Optimized tfs by SaiyansKing https://github.com/mehah/forgottenserver-optimized

`creature:attachEffectById(<effect id>, <temporary>(true | false)) -- Temporary = does not save in character`


##   - 5.2. TFS 1.5: https://github.com/kokekanon/forgottenserver-downgrade/pull/2/files

  ```lua
player:setMapShader(shaderName, [temporary])
player:getMapShader()

creature:setShader(shaderName)
creature:getShader()
creature:detachEffectById(effectId)
creature:attachEffectById(effectId, [temporary])
```

```xml
<monster name="Orc" nameDescription="an orc" race="blood" experience="25" speed="150" manacost="300" raceId="5" shaderEffect = "Outfit - Rainbow" auraEffect = "8" wignsEffect ="11" rayosEffect="7" >

```

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/Orc.png?raw=true" > 

> [!IMPORTANT]
> Active features OTC

```lua
    g_game.enableFeature(GameCreatureAttachedEffect) 

```

##   - 5.3. TFS 1.4.2 : https://github.com/kokekanon/TFS-1.4.2-Compatible-Aura-Effect-Wings-Shader-MEHAH

##   - 5.4. Canary 13.40 : 
