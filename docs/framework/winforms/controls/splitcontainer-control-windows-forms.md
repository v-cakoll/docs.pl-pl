---
title: SplitContainer — Formant (Formularze systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- splitter windows
- SplitContainer control [Windows Forms]
ms.assetid: 2e36f17f-5c39-4fb4-bb09-7ce3ef823402
ms.openlocfilehash: 504a2396902fecf2ac17c2db434fef68ff2ece45
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723663"
---
# <a name="splitcontainer-control-windows-forms"></a><span data-ttu-id="629bb-102">SplitContainer — Formant (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="629bb-102">SplitContainer Control (Windows Forms)</span></span>
<span data-ttu-id="629bb-103">Formularze Windows `SplitContainer` kontrolki mogą być uważane za złożonego, a dwa panele rozdzielone ruchome paska.</span><span class="sxs-lookup"><span data-stu-id="629bb-103">The Windows Forms `SplitContainer` control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="629bb-104">Gdy wskaźnik myszy znajduje się nad paskiem, kursor zmienia kształt, aby pokazać, że pasek jest ruchomy.</span><span class="sxs-lookup"><span data-stu-id="629bb-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="629bb-105">W **przybornika**ten kontrolować zastępuje <xref:System.Windows.Forms.Splitter> formant, który był w poprzedniej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="629bb-105">In the **Toolbox**, this control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of Visual Studio.</span></span> <span data-ttu-id="629bb-106">`SplitContainer` Formant jest znacznie preferowany nad <xref:System.Windows.Forms.Splitter> kontroli.</span><span class="sxs-lookup"><span data-stu-id="629bb-106">The `SplitContainer` control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="629bb-107"><xref:System.Windows.Forms.Splitter> Klasy nadal znajduje się w .NET Framework w celu zachowania zgodności z istniejącymi aplikacjami, ale zdecydowanie zachęcamy do użycia `SplitContainer` kontroli dla nowych projektów.</span><span class="sxs-lookup"><span data-stu-id="629bb-107">The <xref:System.Windows.Forms.Splitter> class is still included in the .NET Framework for compatibility with existing applications, but we strongly encourage you to use the `SplitContainer` control for new projects.</span></span>  
  
 <span data-ttu-id="629bb-108">`SplitContainer` Kontroli pozwala na tworzenie interfejsów użytkownika złożonych; często wybór w jeden panel Określa, jakie obiekty są wyświetlane w innych panelu.</span><span class="sxs-lookup"><span data-stu-id="629bb-108">The `SplitContainer` control lets you create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="629bb-109">Taki układ jest bardzo skuteczny sposób na wyświetlanie i informacji o przeglądaniu.</span><span class="sxs-lookup"><span data-stu-id="629bb-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="629bb-110">Istnienie dwa panele umożliwiają agregują informacje w obszarach i słupka lub "podziału," ułatwia użytkownikom zmieniać rozmiar paneli.</span><span class="sxs-lookup"><span data-stu-id="629bb-110">Having two panels allow you to aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="629bb-111">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="629bb-111">In This Section</span></span>  
 [<span data-ttu-id="629bb-112">SplitContainer, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="629bb-112">SplitContainer Control Overview</span></span>](splitcontainer-control-overview-windows-forms.md)  
 <span data-ttu-id="629bb-113">Wprowadza `SplitContainer` kontroli i zawiera opis często używanych właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="629bb-113">Introduces the `SplitContainer` control and describes the commonly used properties, methods, and events.</span></span>  
  
 [<span data-ttu-id="629bb-114">Instrukcje: Definiowanie zmieniania rozmiaru i pozycjonowania zachowania w podzielonym oknie</span><span class="sxs-lookup"><span data-stu-id="629bb-114">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 <span data-ttu-id="629bb-115">W tym artykule opisano sposób kontrolowania podziału w ramach `SplitContainer` kontroli.</span><span class="sxs-lookup"><span data-stu-id="629bb-115">Describes how to control the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="629bb-116">Instrukcje: Dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="629bb-116">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)  
 <span data-ttu-id="629bb-117">W tym artykule opisano sposób kontrolowania orientacji rozdzielacza w ramach `SplitContainer` kontroli.</span><span class="sxs-lookup"><span data-stu-id="629bb-117">Describes how to control the orientation of the splitter within the `SplitContainer` control.</span></span>  
  
 [<span data-ttu-id="629bb-118">Instrukcje: Tworzenie złożonego interfejsu użytkownika z formularzami Windows</span><span class="sxs-lookup"><span data-stu-id="629bb-118">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="629bb-119">Tworzy interfejs użytkownika wielu okienko, który jest podobny do tego użyć programu Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="629bb-119">Creates a multi-pane user interface that is similar to the one used in Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="629bb-120">Zobacz też [jak: Dzielenie okna w poziomie za pomocą projektanta](how-to-split-a-window-horizontally-using-the-designer.md), [jak: Tworzenie interfejsu w stylu Eksploratora Windows na formularzu Windows](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [jak: Tworzenie złożonego interfejsu użytkownika za pomocą interfejsu Windows Forms przy użyciu narzędzia Projektant](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="629bb-120">Also see [How to: Split a Window Horizontally Using the Designer](how-to-split-a-window-horizontally-using-the-designer.md), [How to: Create a Windows Explorer–Style Interface on a Windows Form](how-to-create-a-windows-explorer-style-interface-on-a-windows-form.md), [How to: Create a Multipane User Interface with Windows Forms Using the Designer](create-a-multipane-user-interface-with-wf-using-the-designer.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="629bb-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="629bb-121">Reference</span></span>  
 <span data-ttu-id="629bb-122"><xref:System.Windows.Forms.SplitContainer> Klasa</span><span class="sxs-lookup"><span data-stu-id="629bb-122"><xref:System.Windows.Forms.SplitContainer> class</span></span>  
 <span data-ttu-id="629bb-123">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="629bb-123">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="629bb-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="629bb-124">Related Sections</span></span>  
 [<span data-ttu-id="629bb-125">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="629bb-125">Windows Forms Controls</span></span>](index.md)  
 <span data-ttu-id="629bb-126">Zawiera łącza do tematów dotyczących kontrolek, zaprojektowany specjalnie w celu pracy z formularzami Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="629bb-126">Provides links to topics about the controls designed specifically to work with Windows Forms.</span></span>  
  
 [<span data-ttu-id="629bb-127">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="629bb-127">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="629bb-128">Zawiera listę wszystkich kontrolek Windows Forms, wraz z łączami do informacji na temat ich używania.</span><span class="sxs-lookup"><span data-stu-id="629bb-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
