---
title: 'Porady: stosowanie wzorca PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 775a27b1b4ba8143e297a3c4d323356a304073a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a><span data-ttu-id="8d6b5-102">Porady: stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="8d6b5-102">How to: Apply the PropertyNameChanged Pattern</span></span>
<span data-ttu-id="8d6b5-103">W poniższym przykładzie kodu pokazano sposób stosowania *PropertyName*zmienione wzorzec do kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="8d6b5-103">The following code example demonstrates how to apply the *PropertyName*Changed pattern to a custom control.</span></span> <span data-ttu-id="8d6b5-104">Podczas implementowania niestandardowych formantów, które są używane przez aparat wiązania danych formularzy systemu Windows, należy zastosować ten wzorzec.</span><span class="sxs-lookup"><span data-stu-id="8d6b5-104">Apply this pattern when you implement custom controls that are used with the Windows Forms data binding engine.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d6b5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d6b5-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d6b5-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8d6b5-106">Compiling the Code</span></span>  
 <span data-ttu-id="8d6b5-107">Aby skompilować w poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="8d6b5-107">To compile the previous code example:</span></span>  
  
-   <span data-ttu-id="8d6b5-108">Wklej kod do pliku kodu puste.</span><span class="sxs-lookup"><span data-stu-id="8d6b5-108">Paste the code into an empty code file.</span></span> <span data-ttu-id="8d6b5-109">Należy używać kontrolki niestandardowej w formularzu systemu Windows, który zawiera `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8d6b5-109">You must use the custom control on a Windows Form that contains a `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6b5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d6b5-110">See Also</span></span>  
 [<span data-ttu-id="8d6b5-111">Instrukcje: implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="8d6b5-111">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 [<span data-ttu-id="8d6b5-112">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d6b5-112">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="8d6b5-113">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d6b5-113">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
