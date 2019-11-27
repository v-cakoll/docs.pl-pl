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
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="f92cf-102">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="f92cf-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="f92cf-103">`ShouldSerialize` i `Reset` są opcjonalnymi metodami, które można podać dla właściwości, jeśli właściwość nie ma prostej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f92cf-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="f92cf-104">Jeśli właściwość ma prostą wartość domyślną, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i podać wartość domyślną konstruktora klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f92cf-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="f92cf-105">Każdy z tych mechanizmów włącza następujące funkcje w projektancie:</span><span class="sxs-lookup"><span data-stu-id="f92cf-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="f92cf-106">Właściwość zapewnia wizualizację wizualną w przeglądarce właściwości, jeśli została zmodyfikowana z wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f92cf-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="f92cf-107">Użytkownik może kliknąć prawym przyciskiem myszy właściwość i wybrać polecenie **Zresetuj** , aby przywrócić wartość domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="f92cf-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="f92cf-108">Projektant generuje bardziej wydajny kod.</span><span class="sxs-lookup"><span data-stu-id="f92cf-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f92cf-109">Zastosuj <xref:System.ComponentModel.DefaultValueAttribute> lub podaj metody `Reset`*PropertyName* i `ShouldSerialize`*PropertyName* .</span><span class="sxs-lookup"><span data-stu-id="f92cf-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="f92cf-110">Nie należy używać obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="f92cf-110">Do not use both.</span></span>

 <span data-ttu-id="f92cf-111">Metoda `Reset`*PropertyName* ustawia właściwość na wartość domyślną, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="f92cf-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="f92cf-112">Jeśli właściwość nie ma metody `Reset`, nie jest oznaczona <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej dostarczonej w swojej deklaracji, opcja `Reset` dla tej właściwości jest wyłączona w menu skrótów okna **właściwości** Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f92cf-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="f92cf-113">Projektanci, takie jak Visual Studio, używają metody `ShouldSerialize`*PropertyName* , aby sprawdzić, czy właściwość została zmieniona z wartości domyślnej i napisać kod w formularzu tylko wtedy, gdy właściwość zostanie zmieniona, co pozwala na bardziej wydajne generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f92cf-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="f92cf-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f92cf-114">For example:</span></span>

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

 <span data-ttu-id="f92cf-115">Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="f92cf-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="f92cf-116">W takim przypadku, nawet gdy wartość zmiennej prywatnej, do której `MyFont` właściwość jest `null`, przeglądarka właściwości nie wyświetla `null`; Zamiast tego wyświetla Właściwość <xref:System.Windows.Forms.Control.Font%2A> elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> zdefiniowaną w <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="f92cf-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="f92cf-117">W rezultacie nie można ustawić wartości domyślnej dla `MyFont` i nie można zastosować <xref:System.ComponentModel.DefaultValueAttribute> do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f92cf-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="f92cf-118">Zamiast tego należy zaimplementować metody `ShouldSerialize` i `Reset` dla właściwości `MyFont`.</span><span class="sxs-lookup"><span data-stu-id="f92cf-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="f92cf-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f92cf-119">See also</span></span>

- [<span data-ttu-id="f92cf-120">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f92cf-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="f92cf-121">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="f92cf-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="f92cf-122">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="f92cf-122">Property-Changed Events</span></span>](property-changed-events.md)
