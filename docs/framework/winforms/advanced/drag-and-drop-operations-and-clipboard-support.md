---
title: Operacje przeciągania i upuszczania oraz obsługa schowka
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: c2bb3c24298ffe5308af03c5af5bae697a22c33b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528617"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="fcf72-102">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="fcf72-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="fcf72-103">Aby umożliwić operacji przeciągania i upuszczania użytkownika w ramach aplikacji opartych na Windows dzięki obsłudze szereg zdarzeń, w szczególności <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fcf72-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="fcf72-104">Możesz również wdrożyć wycinania/kopiowania/wklejania Pomoc dla użytkowników i transfer danych użytkownika do Schowka w aplikacji z systemem Windows przy użyciu wywołania metody proste.</span><span class="sxs-lookup"><span data-stu-id="fcf72-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fcf72-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fcf72-105">In This Section</span></span>  
 [<span data-ttu-id="fcf72-106">Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf72-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="fcf72-107">Wyjaśnia, jak rozpocząć operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcf72-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="fcf72-108">Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="fcf72-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="fcf72-109">Przedstawia sposób wykonania operacji przeciągania i upuszczania między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="fcf72-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="fcf72-110">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="fcf72-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="fcf72-111">W tym artykule opisano sposób programowe wstawianie informacji ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="fcf72-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="fcf72-112">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="fcf72-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="fcf72-113">Opisuje sposób dostępu do danych przechowywanych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="fcf72-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fcf72-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fcf72-114">Related Sections</span></span>  
 [<span data-ttu-id="fcf72-115">Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf72-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="fcf72-116">W tym artykule opisano metody, zdarzenia i klas używany do implementowania zachowanie przeciągnij i upuść.</span><span class="sxs-lookup"><span data-stu-id="fcf72-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="fcf72-117">W tym artykule opisano niewymagającego zdarzenia, które prosi zgody na kontynuowanie działania operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcf72-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="fcf72-118">W tym artykule opisano niewymagającego metodę, która stanowi podstawę do od operacji przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcf72-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="fcf72-119">Zobacz też [porady: wysyłanie danych do Active MDI Child](https://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fcf72-119">Also see [How to: Send Data to the Active MDI Child](https://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>
