---
title: 'Porady: tworzenie formularzy nadrzędnych MDI'
description: Dowiedz się, jak utworzyć formularz nadrzędny MDI programowo i przy użyciu Projektant formularzy systemu Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174708"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="69a35-103">Porady: tworzenie formularzy nadrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="69a35-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69a35-104">W tym temacie jest używany <xref:System.Windows.Forms.MainMenu> formant, który został zastąpiony przez <xref:System.Windows.Forms.MenuStrip> formant.</span><span class="sxs-lookup"><span data-stu-id="69a35-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="69a35-105">W <xref:System.Windows.Forms.MainMenu> przypadku wybrania tej opcji formant jest zachowywany zarówno w przypadku zgodności z poprzednimi wersjami, jak i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="69a35-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="69a35-106">Aby uzyskać informacje na temat tworzenia formularza nadrzędnego MDI przy użyciu <xref:System.Windows.Forms.MenuStrip> , zobacz [How to: Create a MDI Window list with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="69a35-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="69a35-107">Podstawą aplikacji interfejsu wielu dokumentów (MDI) jest formularz nadrzędny MDI.</span><span class="sxs-lookup"><span data-stu-id="69a35-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="69a35-108">Jest to formularz zawierający okna podrzędne MDI, które są podsystemem Windows, w którym użytkownik współdziała z aplikacją MDI.</span><span class="sxs-lookup"><span data-stu-id="69a35-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="69a35-109">Tworzenie formularza nadrzędnego MDI jest proste, zarówno w Projektant formularzy systemu Windows, jak i programowo.</span><span class="sxs-lookup"><span data-stu-id="69a35-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="69a35-110">Utwórz formularz nadrzędny MDI w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="69a35-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="69a35-111">Utwórz projekt aplikacji systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="69a35-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="69a35-112">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Form.IsMdiContainer%2A> Właściwość na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="69a35-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="69a35-113">Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="69a35-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="69a35-114">Podczas ustawiania właściwości w oknie **Właściwości** , można również ustawić `WindowState` Właściwość na **zmaksymalizowane**, jeśli chcesz, ponieważ jest to najłatwiej manipulować oknami podrzędnymi MDI po zmaksymalizowaniu formularza nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="69a35-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="69a35-115">Ponadto należy pamiętać, że krawędź formularza nadrzędnego MDI spowoduje pobranie koloru systemu (ustawianego w panelu sterowania systemu Windows), a nie koloru tyłu ustawianego przy użyciu <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="69a35-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="69a35-116">Z **przybornika**przeciągnij formant **MenuStrip** do formularza.</span><span class="sxs-lookup"><span data-stu-id="69a35-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="69a35-117">Utwórz element menu najwyższego poziomu z właściwością **Text** ustawioną na **&pliku** z elementami podmenu o nazwie **&New** i **&Close**.</span><span class="sxs-lookup"><span data-stu-id="69a35-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="69a35-118">Utwórz także element menu najwyższego poziomu o nazwie **&okno**.</span><span class="sxs-lookup"><span data-stu-id="69a35-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="69a35-119">Pierwsze menu spowoduje utworzenie i ukrycie elementów menu w czasie wykonywania, a drugie menu będzie śledzić otwarte okna podrzędne MDI.</span><span class="sxs-lookup"><span data-stu-id="69a35-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="69a35-120">W tym momencie utworzono okno nadrzędne MDI.</span><span class="sxs-lookup"><span data-stu-id="69a35-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="69a35-121">Naciśnij klawisz **F5** , aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="69a35-121">Press **F5** to run the application.</span></span> <span data-ttu-id="69a35-122">Aby uzyskać informacje na temat tworzenia okien podrzędnych MDI, które działają w ramach formularza nadrzędnego MDI, zobacz [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="69a35-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69a35-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a35-123">See also</span></span>

- [<span data-ttu-id="69a35-124">Aplikacje interfejsu wielu dokumentów (MDI)</span><span class="sxs-lookup"><span data-stu-id="69a35-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="69a35-125">Porady: tworzenie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="69a35-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="69a35-126">Instrukcje: określanie elementu podrzędnego MDI Active</span><span class="sxs-lookup"><span data-stu-id="69a35-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="69a35-127">Instrukcje: wysyłanie danych do Active MDI Child</span><span class="sxs-lookup"><span data-stu-id="69a35-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="69a35-128">Porady: aranżowanie formularzy podrzędnych MDI</span><span class="sxs-lookup"><span data-stu-id="69a35-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
