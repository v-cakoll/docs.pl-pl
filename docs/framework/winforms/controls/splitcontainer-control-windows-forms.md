---
title: SplitContainer — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: d860763e935c88619e3355661038757d00247dfd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963589"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="d0f03-102">SplitContainer — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="d0f03-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="d0f03-103">Formant Windows Forms `SplitContainer` może być uważany za złożony; dwa panele oddzielone przez ruchomy pasek.</span><span class="sxs-lookup"><span data-stu-id="d0f03-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="d0f03-104">Gdy wskaźnik myszy znajduje się nad paskiem, wskaźnik zmieni kształt, aby pokazać, że pasek jest przenośny.</span><span class="sxs-lookup"><span data-stu-id="d0f03-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0f03-105">W **przyborniku**ten formant zastępuje <xref:System.Windows.Forms.Splitter> formant, który był w poprzedniej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0f03-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="d0f03-106">Formant jest dużo preferowany <xref:System.Windows.Forms.Splitter> nad formantem. `SplitContainer`</span><span class="sxs-lookup"><span data-stu-id="d0f03-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="d0f03-107">Klasa jest nadal uwzględniona w .NET Framework w celu zapewnienia zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do `SplitContainer` używania kontrolki dla nowych projektów. <xref:System.Windows.Forms.Splitter></span><span class="sxs-lookup"><span data-stu-id="d0f03-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="d0f03-108">`SplitContainer` Kontrolka umożliwia tworzenie złożonych interfejsów użytkownika. często wybór w jednym panelu określa, jakie obiekty są wyświetlane w drugim panelu.</span><span class="sxs-lookup"><span data-stu-id="d0f03-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="d0f03-109">To rozwiązanie jest bardzo skuteczne do wyświetlania i przeglądania informacji.</span><span class="sxs-lookup"><span data-stu-id="d0f03-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="d0f03-110">Posiadanie dwóch paneli pozwala na agregowanie informacji w obszarach, a pasek lub "rozdzielacz" ułatwia użytkownikom zmianę rozmiaru paneli.</span><span class="sxs-lookup"><span data-stu-id="d0f03-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0f03-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d0f03-111">In This Section</span></span>  
 [<span data-ttu-id="d0f03-112">SplitContainer, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d0f03-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="d0f03-113">`SplitContainer` Wprowadza formant i opisuje najczęściej używane właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d0f03-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="d0f03-114">Instrukcje: Definiowanie zachowania zmiany rozmiaru i pozycjonowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="d0f03-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="d0f03-115">Opisuje sposób kontrolowania rozdzielacza w `SplitContainer` formancie.</span><span class="sxs-lookup"><span data-stu-id="d0f03-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d0f03-116">Instrukcje: Podziel okno w poziomie</span><span class="sxs-lookup"><span data-stu-id="d0f03-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="d0f03-117">Opisuje sposób sterowania orientacją rozdzielacza w `SplitContainer` formancie.</span><span class="sxs-lookup"><span data-stu-id="d0f03-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="d0f03-118">Instrukcje: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0f03-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="d0f03-119">Tworzy wielookienkowy interfejs użytkownika, który jest podobny do tego, który jest używany w programie Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="d0f03-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="d0f03-120">Zapoznaj [się również z tematem: Dzielenie okna w poziomie przy użyciu narzędzia](how-to-split-a-window-horizontally-using-the-designer.md)Projektant [, jak: Tworzenie interfejsu w stylu Eksploratora Windows w formularzu](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md) [systemu Windows: Tworzenie wielookienkowego interfejsu użytkownika z Windows Forms przy użyciu narzędzia](create-a-multipane-user-interface-with-wf-using-the-designer.md)Projektant.</span><span class="sxs-lookup"><span data-stu-id="d0f03-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d0f03-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d0f03-121">Reference</span></span>  
 <span data-ttu-id="d0f03-122"><xref:System.Windows.Forms.SplitContainer>określonej</span><span class="sxs-lookup"><span data-stu-id="d0f03-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="d0f03-123">Opisuje tę klasę i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d0f03-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0f03-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d0f03-124">Related Sections</span></span>  
 [<span data-ttu-id="d0f03-125">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0f03-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="d0f03-126">Zawiera łącza do tematów dotyczących formantów przeznaczonych specjalnie do pracy z Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d0f03-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="d0f03-127">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0f03-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="d0f03-128">Zawiera pełną listę kontrolek Windows Forms, z łączami do informacji o ich użyciu.</span><span class="sxs-lookup"><span data-stu-id="d0f03-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
