---
title: "Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a654fef461d92c4b93db131e303bb07a1e839d34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a><span data-ttu-id="99ddd-102">Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset</span><span class="sxs-lookup"><span data-stu-id="99ddd-102">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>
<span data-ttu-id="99ddd-103">`ShouldSerialize`i `Reset` są opcjonalne metody, które można podać dla właściwości, jeśli właściwość nie ma wartości domyślnej proste.</span><span class="sxs-lookup"><span data-stu-id="99ddd-103">`ShouldSerialize` and `Reset` are optional methods that you can provide for a property, if the property does not a have simple default value.</span></span> <span data-ttu-id="99ddd-104">Jeśli właściwość ma wartość domyślną proste, należy zastosować <xref:System.ComponentModel.DefaultValueAttribute> i zamiast tego Podaj wartość domyślną do konstruktora klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="99ddd-104">If the property has a simple default value, you should apply the <xref:System.ComponentModel.DefaultValueAttribute> and supply the default value to the attribute class constructor instead.</span></span> <span data-ttu-id="99ddd-105">Jedną z tych mechanizmów zapewnia następujące funkcje w Projektancie:</span><span class="sxs-lookup"><span data-stu-id="99ddd-105">Either of these mechanisms enables the following features in the designer:</span></span>  
  
-   <span data-ttu-id="99ddd-106">Właściwość umożliwia oznaczenia wizualne w przeglądarce właściwości, jeśli został on zmodyfikowany ze swojej wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="99ddd-106">The property provides visual indication in the property browser if it has been modified from its default value.</span></span>  
  
-   <span data-ttu-id="99ddd-107">Użytkownik może kliknąć prawym przyciskiem myszy na właściwość i wybierz **zresetować** Aby przywrócić wartość domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="99ddd-107">The user can right-click on the property and choose **Reset** to restore the property to its default value.</span></span>  
  
-   <span data-ttu-id="99ddd-108">Projektant generuje kod większą wydajność.</span><span class="sxs-lookup"><span data-stu-id="99ddd-108">The designer generates more efficient code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99ddd-109">Zastosuj albo <xref:System.ComponentModel.DefaultValueAttribute> lub podaj `Reset` *PropertyName* i `ShouldSerialize` *PropertyName* metody.</span><span class="sxs-lookup"><span data-stu-id="99ddd-109">Either apply the <xref:System.ComponentModel.DefaultValueAttribute> or provide `Reset`*PropertyName* and `ShouldSerialize`*PropertyName* methods.</span></span> <span data-ttu-id="99ddd-110">Nie należy używać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="99ddd-110">Do not use both.</span></span>  
  
 <span data-ttu-id="99ddd-111">`Reset` *PropertyName* — metoda ustawia właściwość na wartość domyślną, jak pokazano w następującego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="99ddd-111">The `Reset`*PropertyName* method sets a property to its default value, as shown in the following code fragment.</span></span>  
  
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
>  <span data-ttu-id="99ddd-112">Jeśli nie ma właściwości `Reset` metody, nie jest oznaczony atrybutem <xref:System.ComponentModel.DefaultValueAttribute>i nie ma wartości domyślnej podana w jego deklaracji `Reset` opcji dla tej właściwości jest wyłączona w menu skrótów **właściwości** okna Projektant formularzy systemu Windows w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99ddd-112">If a property does not have a `Reset` method, is not marked with a <xref:System.ComponentModel.DefaultValueAttribute>, and does not have a default value supplied in its declaration, the `Reset` option for that property is disabled in the shortcut menu of the **Properties** window of the Windows Forms Designer in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="99ddd-113">Projektanci, takich jak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] użyj `ShouldSerialize` *PropertyName* metodę, aby sprawdzić, czy właściwość zmienił się z jej wartości domyślnej i napisać kod do formularza tylko wtedy, gdy właściwość zostanie zmieniona, dzięki czemu większa wydajność Generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="99ddd-113">Designers such as [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] use the `ShouldSerialize`*PropertyName* method to check whether a property has changed from its default value and write code into the form only if a property is changed, thus allowing for more efficient code generation.</span></span> <span data-ttu-id="99ddd-114">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="99ddd-114">For example:</span></span>  
  
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
  
 <span data-ttu-id="99ddd-115">Pełny przykład kodu jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="99ddd-115">A complete code example follows.</span></span>  
  
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
  
 <span data-ttu-id="99ddd-116">W tym przypadku nawet wtedy, gdy dostęp do wartości zmiennej prywatnej `MyFont` właściwość jest `null`, nie są wyświetlane w przeglądarce właściwości `null`; zamiast tego wyświetlana <xref:System.Windows.Forms.Control.Font%2A> właściwości elementu nadrzędnego, jeśli nie jest `null`, lub wartość domyślną <xref:System.Windows.Forms.Control.Font%2A> wartość zdefiniowana w <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="99ddd-116">In this case, even when the value of the private variable accessed by the `MyFont` property is `null`, the property browser does not display `null`; instead, it displays the <xref:System.Windows.Forms.Control.Font%2A> property of the parent, if it is not `null`, or the default <xref:System.Windows.Forms.Control.Font%2A> value defined in <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="99ddd-117">W związku z tym domyślna wartość `MyFont` nie wystarczy można ustawić, a <xref:System.ComponentModel.DefaultValueAttribute> nie można zastosować do tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="99ddd-117">Thus the default value for `MyFont` cannot be simply set, and a <xref:System.ComponentModel.DefaultValueAttribute> cannot be applied to this property.</span></span> <span data-ttu-id="99ddd-118">Zamiast tego `ShouldSerialize` i `Reset` metody musi być zaimplementowana dla `MyFont` właściwości.</span><span class="sxs-lookup"><span data-stu-id="99ddd-118">Instead, the `ShouldSerialize` and `Reset` methods must be implemented for the `MyFont` property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ddd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99ddd-119">See Also</span></span>  
 [<span data-ttu-id="99ddd-120">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="99ddd-120">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="99ddd-121">Definiowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="99ddd-121">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 [<span data-ttu-id="99ddd-122">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="99ddd-122">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)
