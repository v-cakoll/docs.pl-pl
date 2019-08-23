---
title: PrintDocument — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928993"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="5872c-102">PrintDocument — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="5872c-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="5872c-103">Windows Forms składnik [PrintDocument](printdocument-component-windows-forms.md) służy do ustawiania właściwości, które opisują, co należy wydrukować, oraz możliwość drukowania dokumentu w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="5872c-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="5872c-104">Może być używany w połączeniu ze składnikiem [PrintDialog](printdialog-component-windows-forms.md) , aby mieć kontrolę nad wszystkimi aspektami drukowania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="5872c-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="5872c-105">Praca ze składnikiem PrintDocument</span><span class="sxs-lookup"><span data-stu-id="5872c-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="5872c-106">Dwa główne scenariusze obejmujące <xref:System.Drawing.Printing.PrintDocument> składnik to:</span><span class="sxs-lookup"><span data-stu-id="5872c-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="5872c-107">Proste zadania drukowania, takie jak drukowanie pojedynczego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="5872c-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="5872c-108">W takim przypadku należy dodać <xref:System.Drawing.Printing.PrintDocument> składnik do formularza systemu Windows, a następnie dodać logikę programowania, która drukuje plik <xref:System.Drawing.Printing.PrintDocument.PrintPage> w programie obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5872c-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="5872c-109">Logika programowania powinna skutkują z <xref:System.Drawing.Printing.PrintDocument.Print%2A> metodą drukowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5872c-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="5872c-110">Ta metoda wysyła <xref:System.Drawing.Graphics> obiekt znajdujący się <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> we właściwości <xref:System.Drawing.Printing.PrintPageEventArgs> klasy do drukarki.</span><span class="sxs-lookup"><span data-stu-id="5872c-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="5872c-111">Przykład pokazujący sposób drukowania dokumentu tekstowego przy użyciu <xref:System.Drawing.Printing.PrintDocument> składnika można znaleźć w temacie [How to: Drukowanie wielostronicowego pliku tekstowego w Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5872c-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="5872c-112">Bardziej złożone zadania drukowania, takie jak sytuacja, w której chcesz ponownie użyć zapisaną logikę drukowania.</span><span class="sxs-lookup"><span data-stu-id="5872c-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="5872c-113"><xref:System.Drawing.Printing.PrintDocument> W takim przypadku należy utworzyć nowy składnik ze składnika i przesłonić (zobacz [zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md) dla Visual Basic lub przesłonięcia dla C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia. [](../../../csharp/language-reference/keywords/override.md)</span><span class="sxs-lookup"><span data-stu-id="5872c-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="5872c-114">Po dodaniu go do formularza <xref:System.Drawing.Printing.PrintDocument> składnik pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5872c-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="5872c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5872c-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="5872c-116">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5872c-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="5872c-117">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="5872c-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
