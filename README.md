# P6-II-XRToolkit

## Configuración

Se parte del prefab XR Origin (XR Rig), que actúa como base del sistema de entrada y seguimiento del jugador.

Para habilitar la interacción con los controladores, se modificó el mapa de acciones del proyecto:

```
Action Maps → XRI Right Interaction → Select → Add Binding → TriggerButton [RightHand XR Controller]
```

De esta manera, el gatillo del mando derecho se utiliza para seleccionar o agarrar objetos dentro de la escena.

## Interacción a distancia – Cubo lejano

Se añadió el componente, XR Simple Interactable y un script que cambia el color del cubo cada vez que se selecciona:

```csharp
using UnityEngine;
using UnityEngine.XR.Interaction.Toolkit;

public class ChangeColorOnInteract : MonoBehaviour
{
    private Renderer rend;

    void Start()
    {
        rend = GetComponent<Renderer>();   
    }
    
    public void OnSelectEnter()
    {
        Color randomColor = new Color(Random.value, Random.value, Random.value);
        rend.material.color = randomColor;
    }
}
```
Lo asocié manualmente a los eventos del interactuable.

## Interacción cercana – Cubo agarrable

Se añadió el componente, XR Grab Interactable y se utiliza un script simple que muestra un mensaje en la consola al ser agarrado:

```csharp
using UnityEngine;
using UnityEngine.XR.Interaction.Toolkit;

public class MessageOnGrab : MonoBehaviour
{
    public void PrintMessage(SelectEnterEventArgs informationSelect)
    {
        Debug.Log("Grabbed Cube!");
    }
}
```

## Comportamiento final

Comportamiento de la escena en un gif:

![Scene](./Scene.gif)
