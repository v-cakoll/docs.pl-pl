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
ms.openlocfilehash: 609fe4896a2b01b8a69ff8a3d0854c85ddbd6a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969095"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="160b0-102">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="160b0-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="160b0-103">`ShouldSerialize`i `Reset` są opcjonalnymi metodami, które można podać dla właściwości, jeśli właściwość nie ma prostej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="160b0-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="160b0-104">Jeśli właściwość ma prostą wartość domyślną, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i podać wartość domyślną konstruktora klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="160b0-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="160b0-105">Każdy z tych mechanizmów włącza następujące funkcje w projektancie:</span><span class="sxs-lookup"><span data-stu-id="160b0-105">Either of these mechanisms enables the following features in the designer:</span></span>

- <span data-ttu-id="160b0-106">Właściwość zapewnia wizualizację wizualną w przeglądarce właściwości, jeśli została zmodyfikowana z wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="160b0-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>

- <span data-ttu-id="160b0-107">Użytkownik może kliknąć prawym przyciskiem myszy właściwość i wybrać polecenie **Zresetuj** , aby przywrócić wartość domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="160b0-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>

- <span data-ttu-id="160b0-108">Projektant generuje bardziej wydajny kod.</span><span class="sxs-lookup"><span data-stu-id="160b0-108">The designer generates more efficient code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="160b0-109">Zastosuj <xref:System.ComponentModel.DefaultValueAttribute> albo podaj `Reset`metody *PropertyName* i `ShouldSerialize` *PropertyName* .</span><span class="sxs-lookup"><span data-stu-id="160b0-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="160b0-110">Nie należy używać obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="160b0-110">Do not use both.</span></span>

 <span data-ttu-id="160b0-111">Metoda PropertyName ustawia właściwość na wartość domyślną, jak pokazano w poniższym fragmencie kodu. `Reset`</span><span class="sxs-lookup"><span data-stu-id="160b0-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>

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
> <span data-ttu-id="160b0-112">Jeśli `Reset` właściwość nie ma metody, nie jest oznaczona <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej dostarczonej `Reset` w swojej deklaracji, opcja dla tej właściwości jest wyłączona w menu skrótów okna **Właściwości** Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="160b0-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>

 <span data-ttu-id="160b0-113">Projektanci, takie jak Visual Studio, `ShouldSerialize`używają metody *PropertyName* , aby sprawdzić, czy właściwość została zmieniona z wartości domyślnej i napisać kod w formularzu tylko wtedy, gdy właściwość zostanie zmieniona, co pozwala na bardziej wydajne generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="160b0-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="160b0-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="160b0-114">For example:</span></span>

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

 <span data-ttu-id="160b0-115">Poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="160b0-115">A complete code example follows.</span></span>

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

 <span data-ttu-id="160b0-116">W takim przypadku nawet wtedy, gdy wartość zmiennej prywatnej, do której uzyskuje `MyFont` dostęp Właściwość `null`, to przeglądarka właściwości nie jest wyświetlana `null`; zamiast tego wyświetla <xref:System.Windows.Forms.Control.Font%2A> właściwość elementu nadrzędnego, jeśli nie `null`, lub wartość domyślna <xref:System.Windows.Forms.Control.Font%2A> zdefiniowana w. <xref:System.Windows.Forms.Control></span><span class="sxs-lookup"><span data-stu-id="160b0-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="160b0-117">W ten sposób wartość domyślna `MyFont` dla nie może być ustawiona po prostu <xref:System.ComponentModel.DefaultValueAttribute> i nie można jej zastosować do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="160b0-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="160b0-118">Zamiast tego, `ShouldSerialize` metody `Reset` i `MyFont` muszą być zaimplementowane dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="160b0-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>

## <a name="see-also"></a><span data-ttu-id="160b0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="160b0-119">See also</span></span>

- [<span data-ttu-id="160b0-120">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="160b0-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="160b0-121">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="160b0-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="160b0-122">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="160b0-122">Property-Changed Events</span></span>](property-changed-events.md)
