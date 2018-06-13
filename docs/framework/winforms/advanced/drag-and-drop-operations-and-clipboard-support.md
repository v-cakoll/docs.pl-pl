---
title: Operacje przeciągania i upuszczania oraz obsługa schowka
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 05cc79abdeb41cd3bfb7db21ebb206eb309ad5d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522575"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="ace71-102">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="ace71-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="ace71-103">Można włączyć operacji przeciągania i upuszczania użytkownika w aplikacji systemu Windows dzięki obsłudze szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ace71-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="ace71-104">Można też wdrożyć techniczną Wycinanie/kopiowanie/wklejanie użytkownika i transfer danych użytkownika do Schowka w aplikacjach opartych na systemie Windows przy użyciu wywołania metody proste.</span><span class="sxs-lookup"><span data-stu-id="ace71-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ace71-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ace71-105">In This Section</span></span>  
 [<span data-ttu-id="ace71-106">Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace71-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="ace71-107">Wyjaśniono, jak rozpocząć operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="ace71-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="ace71-108">Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="ace71-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="ace71-109">Przedstawiono sposób wykonania operacji przeciągania i upuszczania między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="ace71-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="ace71-110">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="ace71-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="ace71-111">Opisuje sposób programowane wstawianie informacji ze Schowka.</span><span class="sxs-lookup"><span data-stu-id="ace71-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="ace71-112">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="ace71-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="ace71-113">Opisuje sposób dostępu do danych przechowywanych w Schowku.</span><span class="sxs-lookup"><span data-stu-id="ace71-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ace71-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ace71-114">Related Sections</span></span>  
 [<span data-ttu-id="ace71-115">Funkcjonalność przeciągania i upuszczania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace71-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="ace71-116">Opisuje metody, zdarzeń i klasy używane do implementowania zachowanie przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="ace71-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="ace71-117">W tym artykule opisano mogli dokładnie zapoznać się zdarzenia, które żąda uprawnień, aby kontynuować operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="ace71-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="ace71-118">W tym artykule opisano mogli dokładnie zapoznać się metody, która jest podstawą rozpoczyna operację przeciągania.</span><span class="sxs-lookup"><span data-stu-id="ace71-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="ace71-119">Zobacz też [porady: wysyłanie danych do Active podrzędnych MDI](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ace71-119">Also see [How to: Send Data to the Active MDI Child](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>
