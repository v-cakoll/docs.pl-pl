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
ms.openlocfilehash: 11181bacdb919693ffc82c48c061357463a6343b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336762"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset
`ShouldSerialize` i `Reset` są opcjonalnymi metodami, które można podać dla właściwości, jeśli właściwość nie ma prostej wartości domyślnej. Jeśli właściwość ma prostą wartość domyślną, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i podać wartość domyślną konstruktora klasy atrybutu. Każdy z tych mechanizmów włącza następujące funkcje w projektancie:

- Właściwość zapewnia wizualizację wizualną w przeglądarce właściwości, jeśli została zmodyfikowana z wartości domyślnej.

- Użytkownik może kliknąć prawym przyciskiem myszy właściwość i wybrać polecenie **Zresetuj** , aby przywrócić wartość domyślną właściwości.

- Projektant generuje bardziej wydajny kod.

    > [!NOTE]
    > Zastosuj <xref:System.ComponentModel.DefaultValueAttribute> lub podaj metody `Reset`*PropertyName* i `ShouldSerialize`*PropertyName* . Nie należy używać obu tych metod.

 Metoda `Reset`*PropertyName* ustawia właściwość na wartość domyślną, jak pokazano w poniższym fragmencie kodu.

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
> Jeśli właściwość nie ma metody `Reset`, nie jest oznaczona <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej dostarczonej w swojej deklaracji, opcja `Reset` dla tej właściwości jest wyłączona w menu skrótów okna **właściwości** Projektant formularzy systemu Windows w programie Visual Studio.

 Projektanci, takie jak Visual Studio, używają metody `ShouldSerialize`*PropertyName* , aby sprawdzić, czy właściwość została zmieniona z wartości domyślnej i napisać kod w formularzu tylko wtedy, gdy właściwość zostanie zmieniona, co pozwala na bardziej wydajne generowanie kodu. Na przykład:

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

 Poniższy przykład kodu.

```vb
Option Explicit
Option Strict

Imports System.Drawing
Imports System.Windows.Forms

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
using System.Drawing;
using System.Windows.Forms;

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

 W takim przypadku, nawet gdy wartość zmiennej prywatnej, do której `MyFont` właściwość jest `null`, przeglądarka właściwości nie wyświetla `null`; Zamiast tego wyświetla Właściwość <xref:System.Windows.Forms.Control.Font%2A> elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> zdefiniowaną w <xref:System.Windows.Forms.Control>. W rezultacie nie można ustawić wartości domyślnej dla `MyFont` i nie można zastosować <xref:System.ComponentModel.DefaultValueAttribute> do tej właściwości. Zamiast tego należy zaimplementować metody `ShouldSerialize` i `Reset` dla właściwości `MyFont`.

## <a name="see-also"></a>Zobacz także

- [Właściwości kontrolek formularzy Windows Forms](properties-in-windows-forms-controls.md)
- [Definiowanie właściwości](defining-a-property-in-windows-forms-controls.md)
- [Zdarzenia zmiany właściwości](property-changed-events.md)
