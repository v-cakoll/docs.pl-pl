---
title: Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: 23b4ddb3399c12f5bf3c387991676e7ea93b8a29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497436"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset
`ShouldSerialize` i `Reset` metodami Opcjonalnie możesz podać właściwość, jeśli właściwość nie ma wartości domyślnej proste. Jeśli właściwość ma wartość domyślną proste, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i zamiast tego Podaj wartość domyślną do konstruktora klasy atrybutu. Jedną z tych mechanizmów zapewnia następujące funkcje w Projektancie:  
  
-   Właściwość zawiera oznaczenie wizualne w przeglądarce właściwości, jeśli został zmieniony z wartości domyślnej.  
  
-   Użytkownik może kliknąć prawym przyciskiem myszy we właściwości i wybierz **resetowania** można przywrócić właściwości do wartości domyślnej.  
  
-   Projektant generuje kod bardziej wydajne.  
  
    > [!NOTE]
    >  Zastosuj opcję <xref:System.ComponentModel.DefaultValueAttribute> lub podaj `Reset` *PropertyName* i `ShouldSerialize` *PropertyName* metody. Nie należy używać obu.  
  
 `Reset` *PropertyName* metoda ustawia właściwość na wartość domyślną, jak pokazano na następujący fragment kodu.  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  Jeśli nie ma właściwości `Reset` metody, nie jest oznaczony atrybutem <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej podana w jego deklaracji `Reset` opcję dla tej właściwości jest wyłączona w menu skrótów **właściwości** okna Projektanta Windows Forms w programie Visual Studio.  
  
 Użyć projektantów, takich jak Visual Studio `ShouldSerialize` *PropertyName* metodę, aby sprawdzić, czy właściwość został zmieniony z wartości domyślnej i pisanie kodu w formularzu tylko wtedy, gdy właściwość ulegnie zmianie, co pozwala na bardziej efektywne kodu Generowanie. Na przykład:  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 Pełny przykład kodu poniżej.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 W tym przypadku, nawet wtedy, gdy wartość zmiennej prywatnej uzyskiwał dostęp do `MyFont` właściwość `null`, nie są wyświetlane w przeglądarce właściwości `null`; zamiast tego zostanie wyświetlony <xref:System.Windows.Forms.Control.Font%2A> właściwości elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> wartość zdefiniowana w <xref:System.Windows.Forms.Control>. Ten sposób wartością domyślną dla `MyFont` nie można po prostu ustawić i <xref:System.ComponentModel.DefaultValueAttribute> nie można zastosować do tej właściwości. Zamiast tego `ShouldSerialize` i `Reset` metody muszą zostać wdrożone dla `MyFont` właściwości.  
  
## <a name="see-also"></a>Zobacz także
- [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [Definiowanie właściwości](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)
- [Zdarzenia zmiany właściwości](../../../../docs/framework/winforms/controls/property-changed-events.md)
