---
title: 'Instrukcje: Udostępnianie właściwości formantów składowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f3ad37032ee2bb85f37a0eb754277cc9bc040a38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532165"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="33f9c-102">Instrukcje: Udostępnianie właściwości formantów składowych</span><span class="sxs-lookup"><span data-stu-id="33f9c-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="33f9c-103">Noszą nazwę kontrolek, które tworzą kontrolki złożonej *formanty składników*.</span><span class="sxs-lookup"><span data-stu-id="33f9c-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="33f9c-104">Te kontrolki są zwykle zgłaszane w prywatnej, a zatem nie są dostępne przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="33f9c-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="33f9c-105">Jeśli chcesz udostępnić użytkownikom przyszłych właściwości tych kontrolek, należy je udostępnić użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="33f9c-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="33f9c-106">Właściwość składowej formantu jest uwidaczniany przez tworzenie właściwości w kontrolce użytkownika i używanie `get` i `set` metod dostępu właściwości do efektu zmianę właściwości prywatnej składowej formantu.</span><span class="sxs-lookup"><span data-stu-id="33f9c-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="33f9c-107">Należy wziąć pod uwagę kontrolki hipotetyczny użytkownika za pomocą składników przycisk o nazwie `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="33f9c-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="33f9c-108">W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwość, wartość przechowywana we <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="33f9c-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="33f9c-109">Po użytkownik przypisuje wartość tej właściwości, ta wartość jest automatycznie przekazywana do <xref:System.Windows.Forms.Control.BackColor%2A> właściwość `MyButton` i `set` wykona kodu, zmieniając kolor `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="33f9c-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="33f9c-110">Poniższy przykład pokazuje, jak udostępnić <xref:System.Windows.Forms.Control.BackColor%2A> właściwość składowe przycisku:</span><span class="sxs-lookup"><span data-stu-id="33f9c-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="33f9c-111">Aby udostępnić z właściwością kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="33f9c-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="33f9c-112">Utwórz właściwość publiczna dla kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="33f9c-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="33f9c-113">W `get` sekcji właściwości, napisz kod, który pobiera wartość właściwości, którą chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="33f9c-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="33f9c-114">W `set` sekcji właściwości, napisz kod, który przekazuje wartość właściwości do narażonych właściwość składowej formantu.</span><span class="sxs-lookup"><span data-stu-id="33f9c-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f9c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f9c-115">See also</span></span>
- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="33f9c-116">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33f9c-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="33f9c-117">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="33f9c-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
