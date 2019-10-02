---
title: Kodowanie i globalizacja formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
ms.openlocfilehash: 60ca9f7ba2f716b5dab1b0276bc3cd07ddd8f65c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736886"
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="9aec8-102">Kodowanie i globalizacja formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9aec8-102">Encoding and Windows Forms Globalization</span></span>

<span data-ttu-id="9aec8-103">Aplikacje Windows Forms są całkowicie z obsługą standardu Unicode, co oznacza, że każdy znak jest reprezentowany przez unikatową liczbę, niezależnie od rodzaju platformy, programu lub języka.</span><span class="sxs-lookup"><span data-stu-id="9aec8-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="9aec8-104">Aby uzyskać więcej informacji na temat standardu Unicode, zobacz [witrynę sieci Web w standardzie Unicode Consortium](https://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="9aec8-104">For more information about Unicode, see the [Unicode consortium Web site](https://www.unicode.org).</span></span>

## <a name="benefits-of-unicode"></a><span data-ttu-id="9aec8-105">Zalety standardu Unicode</span><span class="sxs-lookup"><span data-stu-id="9aec8-105">Benefits of Unicode</span></span>

<span data-ttu-id="9aec8-106">Zalety formularzy z obsługą standardu Unicode to możliwość pracy ze skryptami, które są tylko w formacie Unicode, takich jak hindi.</span><span class="sxs-lookup"><span data-stu-id="9aec8-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="9aec8-107">Ponadto można użyć wielu języków na jednym formularzu.</span><span class="sxs-lookup"><span data-stu-id="9aec8-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="9aec8-108">W standardzie Unicode wszystkie znaki mają długość dwa bajty, dlatego nie jest konieczne żadne specjalne nakłady do reprezentowania znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="9aec8-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="9aec8-109">Możesz również napisać pojedynczy zestaw kodu, który będzie działał na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="9aec8-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="9aec8-110">Jest to zmiana z wcześniejszych wersji Visual Basic, w których trzeba było napisać inny kod dla różnych platform, takich jak Windows NT i Windows 98.</span><span class="sxs-lookup"><span data-stu-id="9aec8-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and Windows 98.</span></span>

<span data-ttu-id="9aec8-111">Jednak niektóre formanty nie obsługują standardu Unicode w systemach Windows 98 i Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="9aec8-111">However, certain controls do not support Unicode in Windows 98 and Windows Millennium Edition.</span></span> <span data-ttu-id="9aec8-112">Te kontrolki, które dziedziczą ze wspólnej kontrolki, będą przetwarzać dane za pomocą stron kodowych systemu Windows, jako ANSI.</span><span class="sxs-lookup"><span data-stu-id="9aec8-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as ANSI.</span></span> <span data-ttu-id="9aec8-113">Te kontrolki są następujące: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="9aec8-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="9aec8-114">W związku z tym nie można wyświetlać danych Unicode w tych kontrolkach na liście platform.</span><span class="sxs-lookup"><span data-stu-id="9aec8-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="9aec8-115">Nie można na przykład wyświetlić znaków japońskich w angielskiej wersji systemu operacyjnego Windows 98.</span><span class="sxs-lookup"><span data-stu-id="9aec8-115">For example, you cannot display Japanese characters on an English Windows 98 operating system.</span></span>

<span data-ttu-id="9aec8-116">W przypadku rozwiązań z uwzględnieniem standardu Unicode dla kontrolek <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar> należy użyć formantów <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, które zastępują te starsze formanty.</span><span class="sxs-lookup"><span data-stu-id="9aec8-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="9aec8-117">Aby zachować podobny wygląd i działanie między elementami wizualizacji w aplikacji, użyj kontrolki <xref:System.Windows.Forms.MenuStrip> do renderowania menu zamiast <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="9aec8-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="9aec8-118">Podobnie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> może również przetwarzać i wyświetlać znaki Unicode.</span><span class="sxs-lookup"><span data-stu-id="9aec8-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>

## <a name="see-also"></a><span data-ttu-id="9aec8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aec8-119">See also</span></span>

- [<span data-ttu-id="9aec8-120">Globalizacja Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="9aec8-120">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
