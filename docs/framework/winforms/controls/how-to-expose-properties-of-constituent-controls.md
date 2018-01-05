---
title: "Porady: udostępnianie właściwości formantów składowych"
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
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a970864a406f98477fa3e09bdefcf959d2078fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="008a7-102">Porady: udostępnianie właściwości formantów składowych</span><span class="sxs-lookup"><span data-stu-id="008a7-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="008a7-103">Formanty, które tworzą formantu złożonego są nazywane *formanty składników*.</span><span class="sxs-lookup"><span data-stu-id="008a7-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="008a7-104">Tych kontrolek zwykle są deklarowane jako prywatny, a w związku z tym nie można uzyskać dostępu do tych przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="008a7-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="008a7-105">Jeśli chcesz udostępnić użytkownikom przyszłych właściwości tych kontrolek musi ujawniać je użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="008a7-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="008a7-106">Właściwość formantu składników jest udostępniana przez tworzenie właściwości formantu użytkownika i używanie `get` i `set` metody dostępu właściwości dokonanie zmiany właściwości prywatnej składowych formantu.</span><span class="sxs-lookup"><span data-stu-id="008a7-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="008a7-107">Rozważ kontrolkę użytkownika hipotetyczny składowych przycisk o nazwie `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="008a7-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="008a7-108">W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwości, do wartości przechowywanej w <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` jest dostarczany.</span><span class="sxs-lookup"><span data-stu-id="008a7-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="008a7-109">Gdy użytkownik przypisuje wartość do tej właściwości, ta wartość jest automatycznie przekazywane do <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` i `set` kod zostanie wykonany, zmianę koloru `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="008a7-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="008a7-110">Poniższy przykład przedstawia sposób ujawniać <xref:System.Windows.Forms.Control.BackColor%2A> właściwość przycisku składników:</span><span class="sxs-lookup"><span data-stu-id="008a7-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="008a7-111">Do udostępnienia właściwości formantu składników</span><span class="sxs-lookup"><span data-stu-id="008a7-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="008a7-112">Utwórz właściwość publiczna dla formantu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="008a7-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="008a7-113">W `get` sekcji właściwości zapisu kod, który pobiera wartość właściwości chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="008a7-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="008a7-114">W `set` sekcji właściwości zapisu kod, który przekazuje wartość właściwości do ujawnionych właściwości formantu składników.</span><span class="sxs-lookup"><span data-stu-id="008a7-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008a7-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="008a7-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="008a7-116">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="008a7-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="008a7-117">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="008a7-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
