---
title: "Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 514c283575ca54e74d23ae31d3590979be2c3ef0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="15f28-102">Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="15f28-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="15f28-103">Wykonywanie operacji przeciągania i upuszczania między aplikacjami nie różni się od włączenie tej akcji w aplikacji, pod warunkiem, obie aplikacje, które są zaangażowane działają zgodnie z między "kontraktu" <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> i <xref:System.Windows.Forms.DragEventArgs.Effect%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="15f28-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="15f28-104">W poniższej procedurze użyjesz aplikacji systemu Windows, które możesz utworzyć i WordPad edytora tekstów, który jest dołączony do systemu operacyjnego Windows w celu wykonania operacji przeciągania i upuszczania między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="15f28-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="15f28-105">WordPad ma określone dozwolone efekty tekst jest przeciągnięto i Upuszczono; aplikacji systemu Windows, który będzie pisanie kodu dla będzie działać z tych skutków, dzięki czemu może można pomyślnie ukończyć operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="15f28-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="15f28-106">Aby wykonać procedurę przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="15f28-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="15f28-107">Tworzenie nowej aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="15f28-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="15f28-108">Dodaj <xref:System.Windows.Forms.TextBox> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="15f28-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="15f28-109">Skonfiguruj <xref:System.Windows.Forms.TextBox> formantu, aby odbierać dane porzucone.</span><span class="sxs-lookup"><span data-stu-id="15f28-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="15f28-110">Aby uzyskać więcej informacji, zobacz [wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="15f28-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="15f28-111">Uruchamianie aplikacji opartych na systemie Windows, a aplikacja jest uruchomiona, uruchom program WordPad.</span><span class="sxs-lookup"><span data-stu-id="15f28-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="15f28-112">Program WordPad jest zainstalowany w systemie Windows, która zezwala na wykonywanie operacji przeciągania i upuszczania edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="15f28-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="15f28-113">Nie jest dostępny, naciskając klawisz **Start** przycisku, wybierając **Uruchom**, a następnie wpisując `WordPad` w polu tekstowym **Uruchom** okno dialogowe i klikając **OK**.</span><span class="sxs-lookup"><span data-stu-id="15f28-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="15f28-114">Po otwarciu WordPad, wpisz ciąg tekstowy do niego.</span><span class="sxs-lookup"><span data-stu-id="15f28-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="15f28-115">Za pomocą myszy, zaznacz tekst, a następnie przeciągnij zaznaczony tekst do <xref:System.Windows.Forms.TextBox> formantu do aplikacji opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="15f28-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="15f28-116">Który obserwować, gdy wskaźnik myszy zostanie na <xref:System.Windows.Forms.TextBox> formantu (i w związku z tym, zgłoś <xref:System.Windows.Forms.Control.DragEnter> zdarzeń), zmiany kursora, a mogą porzucić zaznaczonego tekstu do <xref:System.Windows.Forms.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="15f28-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="15f28-117">Ponadto można skonfigurować sieci <xref:System.Windows.Forms.TextBox> kontrolki, które umożliwia ciągów tekstowych przeciągnąć i upuścić na WordPad.</span><span class="sxs-lookup"><span data-stu-id="15f28-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="15f28-118">Aby uzyskać więcej informacji, zobacz [wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="15f28-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f28-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f28-119">See Also</span></span>  
 [<span data-ttu-id="15f28-120">Instrukcje: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="15f28-120">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="15f28-121">Instrukcje: pobieranie danych ze schowka</span><span class="sxs-lookup"><span data-stu-id="15f28-121">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="15f28-122">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="15f28-122">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
