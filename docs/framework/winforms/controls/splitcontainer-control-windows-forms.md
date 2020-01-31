---
title: SplitContainer, kontrolka
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: ac04f60847aa6f77c11637f37b5ec94b6f7ef341
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742905"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="50151-102">SplitContainer — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="50151-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="50151-103">Formant Windows Forms `SplitContainer` może być uważany za złożony; jest to dwa panele oddzielone przez ruchomy pasek.</span><span class="sxs-lookup"><span data-stu-id="50151-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="50151-104">Gdy wskaźnik myszy znajduje się nad paskiem, wskaźnik zmieni kształt, aby pokazać, że pasek jest przenośny.</span><span class="sxs-lookup"><span data-stu-id="50151-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50151-105">W **przyborniku**ten formant zastępuje formant <xref:System.Windows.Forms.Splitter>, który był w poprzedniej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50151-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="50151-106">Formant `SplitContainer` jest dużo preferowany nad formantem <xref:System.Windows.Forms.Splitter>.</span><span class="sxs-lookup"><span data-stu-id="50151-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="50151-107">Klasa <xref:System.Windows.Forms.Splitter> nadal jest dołączona do .NET Framework w celu zapewnienia zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do używania kontrolki `SplitContainer` dla nowych projektów.</span><span class="sxs-lookup"><span data-stu-id="50151-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="50151-108">Formant `SplitContainer` umożliwia tworzenie złożonych interfejsów użytkownika. często wybór w jednym panelu określa, jakie obiekty są wyświetlane w drugim panelu.</span><span class="sxs-lookup"><span data-stu-id="50151-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="50151-109">To rozwiązanie jest bardzo skuteczne do wyświetlania i przeglądania informacji.</span><span class="sxs-lookup"><span data-stu-id="50151-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="50151-110">Posiadanie dwóch paneli pozwala na agregowanie informacji w obszarach, a pasek lub "rozdzielacz" ułatwia użytkownikom zmianę rozmiaru paneli.</span><span class="sxs-lookup"><span data-stu-id="50151-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50151-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="50151-111">In This Section</span></span>  
 [<span data-ttu-id="50151-112">SplitContainer, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="50151-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="50151-113">Wprowadza formant `SplitContainer` i opisuje najczęściej używane właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="50151-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="50151-114">Instrukcje: definiowanie zachowania dotyczącego zmieniania rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="50151-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="50151-115">Opisuje sposób kontrolowania rozdzielacza w kontrolce `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="50151-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="50151-116">Instrukcje: dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="50151-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="50151-117">Opisuje sposób sterowania orientacją rozdzielacza w kontrolce `SplitContainer`.</span><span class="sxs-lookup"><span data-stu-id="50151-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="50151-118">Instrukcje: tworzenie złożonego interfejsu użytkownika z formularzami Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50151-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="50151-119">Tworzy wielookienkowy interfejs użytkownika, który jest podobny do tego, który jest używany w programie Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="50151-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="50151-120">Zobacz również [instrukcje: dzielenie okna w poziomie przy użyciu narzędzia Projektant](how-to-split-a-window-horizontally-using-the-designer.md), [jak: Tworzenie interfejsu w stylu Eksploratora Windows w formularzu systemu Windows](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [instrukcje: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms przy użyciu narzędzia Projektant](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="50151-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="50151-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="50151-121">Reference</span></span>  
 <span data-ttu-id="50151-122">Klasa <xref:System.Windows.Forms.SplitContainer></span><span class="sxs-lookup"><span data-stu-id="50151-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="50151-123">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="50151-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="50151-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="50151-124">Related Sections</span></span>  
 [<span data-ttu-id="50151-125">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50151-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="50151-126">Zawiera łącza do tematów dotyczących formantów przeznaczonych specjalnie do pracy z Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="50151-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="50151-127">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50151-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="50151-128">Zawiera pełną listę kontrolek Windows Forms, z łączami do informacji o ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="50151-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
