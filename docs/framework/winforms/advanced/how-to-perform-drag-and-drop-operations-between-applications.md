---
title: 'Instrukcje: Wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 9aac3a0efd6359c25a6972f0e0b52dd489ec31db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003954"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="f35ce-102">Instrukcje: Wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="f35ce-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="f35ce-103">Wykonywanie operacji przeciągania i upuszczania między aplikacjami jest nie różni się od włączania tej akcji w aplikacji, tak długo, jak obie aplikacje, które są zaangażowane zachowują się zgodnie z "Umowy" między <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> i <xref:System.Windows.Forms.DragEventArgs.Effect%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f35ce-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="f35ce-104">W poniższej procedurze użyje tworzonych aplikacji opartych na Windows i program WordPad edytora tekstów, dostępnej w systemie operacyjnym Windows do wykonywania operacji przeciągania i upuszczania między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="f35ce-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="f35ce-105">Program WordPad ma określone dozwolone efekty, że tekst przeciąganie i upuszczanie; Aplikacja oparta na Windows, który trzeba napisać kod, aby uzyskać będzie działać z tych skutków, dzięki czemu może można pomyślnie ukończyć operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="f35ce-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="f35ce-106">Aby wykonać procedurę przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="f35ce-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1. <span data-ttu-id="f35ce-107">Tworzenie nowej aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f35ce-107">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="f35ce-108">Dodaj <xref:System.Windows.Forms.TextBox> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="f35ce-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3. <span data-ttu-id="f35ce-109">Konfigurowanie <xref:System.Windows.Forms.TextBox> kontroli na odbieranie danych porzucone.</span><span class="sxs-lookup"><span data-stu-id="f35ce-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="f35ce-110">Aby uzyskać więcej informacji, zobacz [instruktażu: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f35ce-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4. <span data-ttu-id="f35ce-111">Uruchom aplikację z systemem Windows, a aplikacja jest uruchomiona, uruchom program WordPad.</span><span class="sxs-lookup"><span data-stu-id="f35ce-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="f35ce-112">Program WordPad, jest Edytor tekstu, zainstalowane przez Windows, która umożliwia wykonywanie operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="f35ce-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="f35ce-113">Nie jest dostępny, naciskając klawisz **Start** przycisku, wybierając **Uruchom**, a następnie wpisując `WordPad` w polu tekstowym z **Uruchom** okna dialogowego pole i klikając **OK**.</span><span class="sxs-lookup"><span data-stu-id="f35ce-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5. <span data-ttu-id="f35ce-114">Po otwarciu programu WordPad, wpisz ciąg tekstowy do niego.</span><span class="sxs-lookup"><span data-stu-id="f35ce-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6. <span data-ttu-id="f35ce-115">Za pomocą myszy, zaznacz tekst, a następnie przeciągnij zaznaczony tekst do <xref:System.Windows.Forms.TextBox> kontrolki w aplikacji z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="f35ce-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="f35ce-116">Zauważ, że gdy wskaźnik myszy nad <xref:System.Windows.Forms.TextBox> kontroli (i w związku z tym, wywoływanie <xref:System.Windows.Forms.Control.DragEnter> zdarzeń), zmiany kursora, na które mogą porzucić zaznaczonego tekstu do <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f35ce-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="f35ce-117">Ponadto można skonfigurować usługi <xref:System.Windows.Forms.TextBox> formantu, aby umożliwić ciągów tekstowych można przeciągnąć i upuścić na WordPad.</span><span class="sxs-lookup"><span data-stu-id="f35ce-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="f35ce-118">Aby uzyskać więcej informacji, zobacz [instruktażu: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f35ce-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35ce-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f35ce-119">See also</span></span>

- [<span data-ttu-id="f35ce-120">Instrukcje: Dodawanie danych do Schowka</span><span class="sxs-lookup"><span data-stu-id="f35ce-120">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="f35ce-121">Instrukcje: Pobieranie danych ze Schowka</span><span class="sxs-lookup"><span data-stu-id="f35ce-121">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="f35ce-122">Operacje przeciągania i upuszczania oraz obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="f35ce-122">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
