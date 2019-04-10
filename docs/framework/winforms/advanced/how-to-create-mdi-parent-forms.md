---
title: 'Instrukcje: Tworzenie formularzy nadrzędnych MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d3ec2e16f06169790711c92c9d445ae93ee50c95
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338660"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="2ef5e-102">Instrukcje: Tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="2ef5e-102">How to: Create MDI Parent Forms</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="2ef5e-103">W tym temacie używany <xref:System.Windows.Forms.MainMenu> formant, który został zastąpiony przez <xref:System.Windows.Forms.MenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-103">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="2ef5e-104"><xref:System.Windows.Forms.MainMenu> Kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-104">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span>  <span data-ttu-id="2ef5e-105">Informacje o tworzeniu MDI nadrzędnego formularza za pomocą <xref:System.Windows.Forms.MenuStrip>, zobacz [jak: Tworzenie List okien MDI za pomocą elementu MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2ef5e-105">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>  
  
 <span data-ttu-id="2ef5e-106">Podstawą aplikacji interfejsu wielu dokumentów (MDI) jest formularza nadrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-106">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="2ef5e-107">Jest to formularz, który zawiera oknami podrzędnymi MDI, które są podrzędne windows, w którym użytkownik wchodzi w interakcję z aplikacją MDI.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-107">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="2ef5e-108">Tworzenie formularza nadrzędnego MDI jest łatwe, zarówno w programie Windows Forms Designer, jak i programowo.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-108">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="2ef5e-109">Aby utworzyć formularza nadrzędnego MDI w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="2ef5e-109">To create an MDI parent form at design time</span></span>  
  
1. <span data-ttu-id="2ef5e-110">Utwórz projekt aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-110">Create a Windows Application project.</span></span>  
  
2. <span data-ttu-id="2ef5e-111">W **właściwości** oknie <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości **true**.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-111">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>  
  
     <span data-ttu-id="2ef5e-112">Określa formularza jako kontenera okien podrzędnych MDI.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-112">This designates the form as an MDI container for child windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ef5e-113">Podczas ustawiania właściwości w **właściwości** okna, można również ustawić `WindowState` właściwości **Maximized**, jeśli chcesz, ponieważ jest najprostszym manipulować oknami podrzędnymi MDI, gdy formularz nadrzędny jest zmaksymalizowany.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-113">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="2ef5e-114">Ponadto należy pamiętać, że krawędzi formularza nadrzędnego MDI przejmą kolorów systemu (zestaw w Panelu sterowania systemu Windows), zamiast kolor tyłu można ustawić za pomocą <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-114">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>  
  
3. <span data-ttu-id="2ef5e-115">Z **przybornika**, przeciągnij **MenuStrip** formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-115">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="2ef5e-116">Utwórz element menu najwyższego poziomu za pomocą **tekstu** właściwością **& plik** ze wskazaniem elementów podmenu **& nowe** i **i Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-116">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="2ef5e-117">Również utworzyć menu najwyższego poziomu elementu o nazwie **& okna**.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-117">Also create a top-level menu item called **&Window**.</span></span>  
  
     <span data-ttu-id="2ef5e-118">Pierwszym menu spowoduje to utworzenie i ukrywanie elementów menu w czasie wykonywania, i drugiego menu będzie śledzenie otwarte okna podrzędnego MDI.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-118">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="2ef5e-119">Na tym etapie utworzono nadrzędnego okna MDI.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-119">At this point, you have created an MDI parent window.</span></span>  
  
4. <span data-ttu-id="2ef5e-120">Naciśnij klawisz **F5** do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2ef5e-120">Press **F5** to run the application.</span></span> <span data-ttu-id="2ef5e-121">Aby uzyskać informacje dotyczące tworzenia elementu podrzędnego MDI systemu windows, które działają w ramach formularza nadrzędnego MDI, zobacz [jak: Tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2ef5e-121">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef5e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ef5e-122">See also</span></span>

- [<span data-ttu-id="2ef5e-123">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="2ef5e-123">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="2ef5e-124">Instrukcje: Tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="2ef5e-124">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="2ef5e-125">Instrukcje: Określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="2ef5e-125">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="2ef5e-126">Instrukcje: Wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="2ef5e-126">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="2ef5e-127">Instrukcje: Rozmieszczanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="2ef5e-127">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
