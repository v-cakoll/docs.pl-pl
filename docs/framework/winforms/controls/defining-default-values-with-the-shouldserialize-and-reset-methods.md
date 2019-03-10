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
ms.openlocfilehash: 2cb23220be2b4a3564c4869016c05065afe7c27c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704475"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="ff33c-102">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="ff33c-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="ff33c-103">`ShouldSerialize` i `Reset` metodami Opcjonalnie możesz podać właściwość, jeśli właściwość nie ma wartości domyślnej proste.</span><span class="sxs-lookup"><span data-stu-id="ff33c-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="ff33c-104">Jeśli właściwość ma wartość domyślną proste, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i zamiast tego Podaj wartość domyślną do konstruktora klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ff33c-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="ff33c-105">Jedną z tych mechanizmów zapewnia następujące funkcje w Projektancie:</span><span class="sxs-lookup"><span data-stu-id="ff33c-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="ff33c-106">Właściwość zawiera oznaczenie wizualne w przeglądarce właściwości, jeśli został zmieniony z wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff33c-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="ff33c-107">Użytkownik może kliknąć prawym przyciskiem myszy we właściwości i wybierz **resetowania** można przywrócić właściwości do wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ff33c-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="ff33c-108">Projektant generuje kod bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="ff33c-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ff33c-109">Zastosuj opcję <xref:System.ComponentModel.DefaultValueAttribute> lub podaj `Reset` *PropertyName* i `ShouldSerialize` *PropertyName* metody.</span><span class="sxs-lookup"><span data-stu-id="ff33c-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="ff33c-110">Nie należy używać obu.</span><span class="sxs-lookup"><span data-stu-id="ff33c-110">Do not use both.</span></span>  
  
 <span data-ttu-id="ff33c-111">`Reset` *PropertyName* metoda ustawia właściwość na wartość domyślną, jak pokazano na następujący fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="ff33c-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="ff33c-112">Jeśli nie ma właściwości `Reset` metody, nie jest oznaczony atrybutem <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej podana w jego deklaracji `Reset` opcję dla tej właściwości jest wyłączona w menu skrótów **właściwości** okna Projektanta Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ff33c-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in Visual Studio.</span></span>  
  
 <span data-ttu-id="ff33c-113">Użyć projektantów, takich jak Visual Studio `ShouldSerialize` *PropertyName* metodę, aby sprawdzić, czy właściwość został zmieniony z wartości domyślnej i pisanie kodu w formularzu tylko wtedy, gdy właściwość ulegnie zmianie, co pozwala na bardziej efektywne kodu Generowanie.</span><span class="sxs-lookup"><span data-stu-id="ff33c-113">Designers such as Visual Studio use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="ff33c-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ff33c-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="ff33c-115">Pełny przykład kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="ff33c-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="ff33c-116">W tym przypadku, nawet wtedy, gdy wartość zmiennej prywatnej uzyskiwał dostęp do `MyFont` właściwość `null`, nie są wyświetlane w przeglądarce właściwości `null`; zamiast tego zostanie wyświetlony <xref:System.Windows.Forms.Control.Font%2A> właściwości elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> wartość zdefiniowana w <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="ff33c-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="ff33c-117">Ten sposób wartością domyślną dla `MyFont` nie można po prostu ustawić i <xref:System.ComponentModel.DefaultValueAttribute> nie można zastosować do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff33c-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="ff33c-118">Zamiast tego `ShouldSerialize` i `Reset` metody muszą zostać wdrożone dla `MyFont` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ff33c-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff33c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff33c-119">See also</span></span>
- [<span data-ttu-id="ff33c-120">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ff33c-120">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="ff33c-121">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="ff33c-121">Defining a Property</span></span>](defining-a-property-in-windows-forms-controls.md)
- [<span data-ttu-id="ff33c-122">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="ff33c-122">Property-Changed Events</span></span>](property-changed-events.md)
