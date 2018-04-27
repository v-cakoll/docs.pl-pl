---
title: Kodowanie i globalizacja formularzy systemu Windows
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16e54e1915370549124c202bce6ad09c4aca1a40
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="encoding-and-windows-forms-globalization"></a><span data-ttu-id="64321-102">Kodowanie i globalizacja formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="64321-102">Encoding and Windows Forms Globalization</span></span>
<span data-ttu-id="64321-103">Aplikacji formularzy systemu Windows są całkowicie obsługą Unicode, co oznacza, że każdy znak jest reprezentowany przez unikatowy numer, niezależnie od tego, jakie platformy, program lub języka.</span><span class="sxs-lookup"><span data-stu-id="64321-103">Windows Forms applications are entirely Unicode-enabled, meaning that each character is represented by a unique number, no matter what the platform, program, or language.</span></span> <span data-ttu-id="64321-104">Aby uzyskać więcej informacji na temat Unicode, zobacz [witryny sieci Web konsorcjum Unicode](http://www.unicode.org).</span><span class="sxs-lookup"><span data-stu-id="64321-104">For more information about Unicode, see the [Unicode consortium Web site](http://www.unicode.org).</span></span>  
  
## <a name="benefits-of-unicode"></a><span data-ttu-id="64321-105">Korzyści wynikające z Unicode</span><span class="sxs-lookup"><span data-stu-id="64321-105">Benefits of Unicode</span></span>  
 <span data-ttu-id="64321-106">Zalety formularze obsługujące format Unicode możliwość pracy ze skryptami, które są tylko Unicode, takich jak Hindi.</span><span class="sxs-lookup"><span data-stu-id="64321-106">The benefits of Unicode-enabled forms include the ability to work with scripts that are Unicode-only, such as Hindi.</span></span> <span data-ttu-id="64321-107">Ponadto można użyć wielu języków w formie jednej.</span><span class="sxs-lookup"><span data-stu-id="64321-107">In addition, you can use multiple languages on a single form.</span></span> <span data-ttu-id="64321-108">W formacie Unicode wszystkie znaki są dwa bajty, więc nie jest wymagane nie specjalne działania do reprezentowania znaków dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="64321-108">In Unicode, all characters are two bytes long, so no special effort is needed to represent double-byte characters.</span></span> <span data-ttu-id="64321-109">Można również napisać kod, który będzie działać na wszystkich platformach jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="64321-109">You can also write a single set of code that will work on all platforms.</span></span> <span data-ttu-id="64321-110">Jest to zmiana z poprzednich wersji programu Visual Basic, masz do pisania różnych kodu dla różnych platform, takich jak Windows NT i [!INCLUDE[win98](../../../../includes/win98-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64321-110">This is a change from previous versions of Visual Basic, in which you had to write different code for different platforms, such as Windows NT and [!INCLUDE[win98](../../../../includes/win98-md.md)].</span></span>  
  
 <span data-ttu-id="64321-111">Jednak niektóre formanty nie obsługują standardu Unicode w [!INCLUDE[win98](../../../../includes/win98-md.md)] i Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="64321-111">However, certain controls do not support Unicode in [!INCLUDE[win98](../../../../includes/win98-md.md)] and Windows Millennium Edition.</span></span> <span data-ttu-id="64321-112">Tych kontrolek, które dziedziczą z formantu wspólnego, będzie przetwarzać danych za pomocą stron kodowych systemu Windows jako [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64321-112">These controls, all of which inherit from the common control, will process data with the Windows code pages, as [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)].</span></span> <span data-ttu-id="64321-113">Te procedury są: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, i <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="64321-113">These controls are: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, and <xref:System.Windows.Forms.StatusBar>.</span></span> <span data-ttu-id="64321-114">W związku z tym nie można wyświetlić danych Unicode w tych kontrolek w wymienionych platform.</span><span class="sxs-lookup"><span data-stu-id="64321-114">As a result, you cannot display Unicode data in these controls on the listed platforms.</span></span> <span data-ttu-id="64321-115">Na przykład nie można wyświetlić japońskie znaki w języku angielskim [!INCLUDE[win98](../../../../includes/win98-md.md)] systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="64321-115">For example, you cannot display Japanese characters on an English [!INCLUDE[win98](../../../../includes/win98-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="64321-116">Dla obsługujących Unicode alternatywy dla <xref:System.Windows.Forms.ToolBar> i <xref:System.Windows.Forms.StatusBar> formantów, użyj <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip> formanty, które Zastąp tych starszych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="64321-116">For Unicode-aware alternatives to the <xref:System.Windows.Forms.ToolBar> and <xref:System.Windows.Forms.StatusBar> controls, use the <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip> controls, which replace these older controls.</span></span> <span data-ttu-id="64321-117">Aby zachować podobne wygląd i działanie między elementy wizualne w aplikacji, należy użyć <xref:System.Windows.Forms.MenuStrip> kontroli w przypadku renderowania menu zamiast <xref:System.Windows.Forms.MainMenu>.</span><span class="sxs-lookup"><span data-stu-id="64321-117">To maintain a similar look and feel between visual elements in your application, use the <xref:System.Windows.Forms.MenuStrip> control for rendering menus instead of <xref:System.Windows.Forms.MainMenu>.</span></span> <span data-ttu-id="64321-118">Podobnie jak <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> można również przetwarzanie i wyświetlanie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="64321-118">Like <xref:System.Windows.Forms.ToolStrip> and <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> can also process and display Unicode characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64321-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64321-119">See Also</span></span>  
 [<span data-ttu-id="64321-120">Globalizacja formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64321-120">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
