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
ms.openlocfilehash: 36670eee6235277a7fe98770192df9ae05d3dd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966819"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="7de90-102">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="7de90-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="7de90-103">Poniższy przykład kodu demonstruje sposób stosowania *PropertyName*wzorzec zmieniono formant niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="7de90-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="7de90-104">Zastosowanie tego wzorca, gdy implementują niestandardowe formanty, które są używane z aparatem powiązanie danych formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="7de90-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de90-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7de90-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7de90-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7de90-106">Compiling the Code</span></span>  
 <span data-ttu-id="7de90-107">Aby skompilować w poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="7de90-107">To compile the previous code example:</span></span>  
  
- <span data-ttu-id="7de90-108">Wklej kod do pliku kodu puste.</span><span class="sxs-lookup"><span data-stu-id="7de90-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="7de90-109">Należy użyć niestandardowego formantu w formularzu Windows, który zawiera `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7de90-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de90-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7de90-110">See also</span></span>

- [<span data-ttu-id="7de90-111">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="7de90-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)
- [<span data-ttu-id="7de90-112">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7de90-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="7de90-113">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7de90-113">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
