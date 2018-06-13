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
ms.openlocfilehash: 8d7645e8de5edee711c30bbe7edde8ba7b5b1dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529795"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset
`ShouldSerialize` i `Reset` są opcjonalne metody, które można podać dla właściwości, jeśli właściwość nie ma wartości domyślnej proste. Jeśli właściwość ma wartość domyślną proste, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i zamiast tego Podaj wartość domyślną do konstruktora klasy atrybutu. Jedną z tych mechanizmów zapewnia następujące funkcje w Projektancie:  
  
-   Właściwość umożliwia oznaczenia wizualne w przeglądarce właściwości, jeśli został on zmodyfikowany ze swojej wartości domyślnej.  
  
-   Użytkownik może kliknąć prawym przyciskiem myszy na właściwość i wybierz **zresetować** Aby przywrócić wartość domyślną właściwości.  
  
-   Projektant generuje kod większą wydajność.  
  
    > [!NOTE]
    >  Zastosuj albo <xref:System.ComponentModel.DefaultValueAttribute> lub podaj `Reset` *PropertyName* i `ShouldSerialize` *PropertyName* metody. Nie należy używać jednocześnie.  
  
 `Reset` *PropertyName* — metoda ustawia właściwość na wartość domyślną, jak pokazano w następującego fragmentu kodu.  
  
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
>  Jeśli nie ma właściwości `Reset` metody, nie jest oznaczony atrybutem <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej podana w jego deklaracji `Reset` opcji dla tej właściwości jest wyłączona w menu skrótów **właściwości** okna Projektant formularzy systemu Windows w programie Visual Studio.  
  
 Użyj projektantów, takiego jak Visual Studio `ShouldSerialize` *PropertyName* metodę, aby sprawdzić, czy właściwość zmienił się z jej wartości domyślnej i napisać kod do formularza tylko wtedy, gdy właściwość zostanie zmieniona, dzięki czemu efektywniejsze kodu Generowanie. Na przykład:  
  
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
  
 Pełny przykład kodu jest zgodna.  
  
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
  
 W tym przypadku nawet wtedy, gdy dostęp do wartości zmiennej prywatnej `MyFont` właściwość jest `null`, nie są wyświetlane w przeglądarce właściwości `null`; zamiast tego wyświetlana <xref:System.Windows.Forms.Control.Font%2A> właściwości elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> wartość zdefiniowana w <xref:System.Windows.Forms.Control>. W związku z tym domyślna wartość `MyFont` nie wystarczy można ustawić, a <xref:System.ComponentModel.DefaultValueAttribute> nie można zastosować do tej właściwości. Zamiast tego `ShouldSerialize` i `Reset` metody musi być zaimplementowana dla `MyFont` właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Definiowanie właściwości](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [Zdarzenia zmiany właściwości](../../../../docs/framework/winforms/controls/property-changed-events.md)
