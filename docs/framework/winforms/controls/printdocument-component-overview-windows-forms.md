---
title: PrintDocument — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728541"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="7359a-102">PrintDocument — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="7359a-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="7359a-103">Windows Forms składnik [PrintDocument](printdocument-component-windows-forms.md) służy do ustawiania właściwości, które opisują, co należy wydrukować, oraz możliwość drukowania dokumentu w aplikacjach opartych na systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="7359a-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="7359a-104">Może być używany w połączeniu ze składnikiem [PrintDialog](printdialog-component-windows-forms.md) , aby mieć kontrolę nad wszystkimi aspektami drukowania dokumentów.</span><span class="sxs-lookup"><span data-stu-id="7359a-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="7359a-105">Praca ze składnikiem PrintDocument</span><span class="sxs-lookup"><span data-stu-id="7359a-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="7359a-106">Dwa główne scenariusze obejmujące składnik <xref:System.Drawing.Printing.PrintDocument> są następujące:</span><span class="sxs-lookup"><span data-stu-id="7359a-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="7359a-107">Proste zadania drukowania, takie jak drukowanie pojedynczego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="7359a-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="7359a-108">W takim przypadku należy dodać składnik <xref:System.Drawing.Printing.PrintDocument> do formularza systemu Windows, a następnie dodać logikę programowania, która drukuje plik w programie obsługi zdarzeń <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7359a-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="7359a-109">Logika programowania powinna skutkują z metodą <xref:System.Drawing.Printing.PrintDocument.Print%2A>, aby wydrukować dokument.</span><span class="sxs-lookup"><span data-stu-id="7359a-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="7359a-110">Ta metoda wysyła <xref:System.Drawing.Graphics> obiektu znajdującego się we właściwości <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> klasy <xref:System.Drawing.Printing.PrintPageEventArgs> do drukarki.</span><span class="sxs-lookup"><span data-stu-id="7359a-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="7359a-111">Przykład pokazujący sposób drukowania dokumentu tekstowego przy użyciu składnika <xref:System.Drawing.Printing.PrintDocument>, zobacz [How to: Print a wielostronicowy plik tekstowy w Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7359a-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="7359a-112">Bardziej złożone zadania drukowania, takie jak sytuacja, w której chcesz ponownie użyć zapisaną logikę drukowania.</span><span class="sxs-lookup"><span data-stu-id="7359a-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="7359a-113">W takim przypadku należy utworzyć nowy składnik ze składnika <xref:System.Drawing.Printing.PrintDocument> i przesłonić (zobacz [zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md) dla Visual Basic lub [przesłonięcia](../../../csharp/language-reference/keywords/override.md) dla C#) zdarzenia <xref:System.Drawing.Printing.PrintDocument.PrintPage>.</span><span class="sxs-lookup"><span data-stu-id="7359a-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="7359a-114">Po dodaniu do formularza składnik <xref:System.Drawing.Printing.PrintDocument> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7359a-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="7359a-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7359a-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="7359a-116">Obsługa drukowania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7359a-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="7359a-117">PrintDocument, składnik</span><span class="sxs-lookup"><span data-stu-id="7359a-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
