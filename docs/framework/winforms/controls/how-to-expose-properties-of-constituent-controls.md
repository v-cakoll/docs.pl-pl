---
title: 'Instrukcje: udostępnianie właściwości kontrolek składowych'
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
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015876"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="09b25-102">Instrukcje: udostępnianie właściwości kontrolek składowych</span><span class="sxs-lookup"><span data-stu-id="09b25-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="09b25-103">Kontrolki wchodzące w skład formantu złożonego są nazywane *kontrolkami elementów*.</span><span class="sxs-lookup"><span data-stu-id="09b25-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="09b25-104">Te kontrolki są zwykle zadeklarowane jako prywatne i w tym przypadku nie są dostępne dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="09b25-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="09b25-105">Jeśli chcesz, aby właściwości tych kontrolek były dostępne dla przyszłych użytkowników, musisz uwidocznić je użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="09b25-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="09b25-106">Właściwość kontrolki elementu jest uwidaczniana przez utworzenie właściwości w kontrolce użytkownika i użycie `get` metod i `set` dostępu tej właściwości, aby zmienić właściwość prywatną kontrolki elementu.</span><span class="sxs-lookup"><span data-stu-id="09b25-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>

 <span data-ttu-id="09b25-107">Rozważmy hipotetyczny formant użytkownika z przyciskiem składnika o `MyButton`nazwie.</span><span class="sxs-lookup"><span data-stu-id="09b25-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="09b25-108">W tym przykładzie, gdy użytkownik zażąda `ConstituentButtonBackColor` właściwości, `MyButton` zostanie wykazana wartość przechowywana <xref:System.Windows.Forms.Control.BackColor%2A> we właściwości.</span><span class="sxs-lookup"><span data-stu-id="09b25-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="09b25-109">Gdy użytkownik przypisuje wartość do tej właściwości, ta wartość jest <xref:System.Windows.Forms.Control.BackColor%2A> automatycznie przenoszona do `MyButton` właściwości, a `set` `MyButton`kod zostanie wykonany, zmieniając kolor.</span><span class="sxs-lookup"><span data-stu-id="09b25-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>

 <span data-ttu-id="09b25-110">Poniższy przykład pokazuje, <xref:System.Windows.Forms.Control.BackColor%2A> jak uwidocznić właściwość przycisku składnik:</span><span class="sxs-lookup"><span data-stu-id="09b25-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>

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

### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="09b25-111">Aby uwidocznić właściwość formantu składnika</span><span class="sxs-lookup"><span data-stu-id="09b25-111">To expose a property of a constituent control</span></span>

1. <span data-ttu-id="09b25-112">Utwórz Właściwość publiczną dla kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="09b25-112">Create a public property for your user control.</span></span>

2. <span data-ttu-id="09b25-113">`get` W sekcji Właściwości Napisz kod, który pobiera wartość właściwości, którą chcesz uwidocznić.</span><span class="sxs-lookup"><span data-stu-id="09b25-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>

3. <span data-ttu-id="09b25-114">`set` W sekcji Właściwości Napisz kod, który przekazuje wartość właściwości do właściwości uwidocznionej kontrolki składnik.</span><span class="sxs-lookup"><span data-stu-id="09b25-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>

## <a name="see-also"></a><span data-ttu-id="09b25-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09b25-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="09b25-116">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09b25-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="09b25-117">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="09b25-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
