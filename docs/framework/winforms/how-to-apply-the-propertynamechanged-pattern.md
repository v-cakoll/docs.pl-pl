---
title: 'Instrukcje: Stosowanie wzorca PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 82856405ab3c9581b398f358e5bf9ecf989ce193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539769"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="c0d27-102">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="c0d27-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="c0d27-103">Poniższy przykład kodu demonstruje sposób stosowania *PropertyName*wzorzec zmieniono formant niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="c0d27-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="c0d27-104">Zastosowanie tego wzorca, gdy implementują niestandardowe formanty, które są używane z aparatem powiązanie danych formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="c0d27-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0d27-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c0d27-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0d27-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c0d27-106">Compiling the Code</span></span>  
 <span data-ttu-id="c0d27-107">Aby skompilować w poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="c0d27-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="c0d27-108">Wklej kod do pliku kodu puste.</span><span class="sxs-lookup"><span data-stu-id="c0d27-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="c0d27-109">Należy użyć niestandardowego formantu w formularzu Windows, który zawiera `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c0d27-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0d27-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0d27-110">See also</span></span>
- [<span data-ttu-id="c0d27-111">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="c0d27-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="c0d27-112">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0d27-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="c0d27-113">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0d27-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
