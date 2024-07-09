
## Table of Contents
1. [Register](#register)

   1.1. [Category](#category)

   1.2. [Properties](#properties)

2. [Creature](#creature)

   2.1. [UIcreature](#uicreature)

   2.2. [Creature](#creature2)

3. [Widget](#widget)
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
    `register(id, name, thingId, thingType, config)`
    `config = {`
        `speed, disableWalkAnimation, shader, drawOnUI, opacity`
        `duration, loop, transform, hideOwner, size{width, height}`
        `offset{x, y, onTop}, dirOffset[dir]{x, y, onTop},`
        `light { color, intensity}, drawOrder(only for tiles),`
        `bounce{minHeight, height, speed}`
        `onAttach, onDetach`
    `}`
`]]
```
--

### <a name="properties"> 1.2 Properties</a>
_speed_:

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_speed_.gif?raw=true" > 




_disableWalkAnimation_


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_disableWalkAnimation_.gif?raw=true" > 

_shader_


<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_shader_.gif?raw=true" > 


_drawOnUI_

`coming soon`

_opacity_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_opacity_.gif?raw=true" > 


_duration_

`coming soon`

_transform_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_transform_.gif?raw=true" > 



_loop_

`coming soon`

_hideOwner_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_hideOwner_.gif?raw=true" > 


_size (only textures)_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_size_.gif?raw=true" > 


_offset (only textures)_

`coming soon`


_dirOffset_ (only ThingCategoryCreature , ThingCategoryEffect)

horizontal

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/horizontal.gif?raw=true" > 



vertical

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/vertical.gif?raw=true" > 

_light_

`coming soon`

_drawOrder_

`coming soon`

_bounce_

<img src="https://github.com/kokekanon/OTredemption-Picture-NODELETE/blob/main/Wiki/_bounce_.gif?raw=true" > 

_onAttach_

`coming soon`

_onDetach_

`coming soon`

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

###   <a name="Creature2">    - 2.2. Creature:</a>

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


# <a name="widget"> 3.- Widget</a>


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


<video src="https://github.com/Nottinghster/otclient/assets/114332266/9ee58399-5832-42e3-acc9-f15c6cd831fd" width="600" controls></video>

# <a name="Particle"> 4.- Particle</a>
```lua
g_game.getLocalPlayer():attachParticleEffect("creature-effect")
```
![image](https://github.com/kokekanon/OTredemption-Picture-NODELETE/raw/main/Picture/Attached%20Effect/Creature/003_particula.gif?raw=true)



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
##   - 5.3. Canary 13.32 : 
