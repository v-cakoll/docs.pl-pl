---
title: 'Instrukcje: Blokowanie kontrolek do formularzy Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: a59e5997104b9438681702d460dd8f6937df41b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741460"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="38837-102">Instrukcje: Blokowanie kontrolek do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38837-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="38837-103">Podczas projektowania interfejsu użytkownika (UI) w aplikacji Windows, można zablokować kontrolki po znajdują się one poprawnie, tak aby wątkami aby przypadkowo nie przenosić lub zmieniać ich rozmiar przy ustawianiu inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="38837-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="38837-104">Ponadto można zablokować i odblokować wszystkie formanty w formularzu jednocześnie, co jest przydatne w przypadku formularzy z wieloma formantami, albo można odblokować pojedynczych formantów.</span><span class="sxs-lookup"><span data-stu-id="38837-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="38837-105">Po umieszczeniu wszystkich kontrolek odpowiednie miejsca w formularzu, należy zablokować je w miejscu, aby uniknąć przenoszenia błędne.</span><span class="sxs-lookup"><span data-stu-id="38837-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38837-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="38837-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="38837-107">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="38837-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="38837-108">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="38837-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="38837-109">Aby zablokować kontrolki</span><span class="sxs-lookup"><span data-stu-id="38837-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="38837-110">W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `true`.</span><span class="sxs-lookup"><span data-stu-id="38837-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="38837-111">(Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).</span><span class="sxs-lookup"><span data-stu-id="38837-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="38837-112">Alternatywnie, kliknij prawym przyciskiem myszy formant i wybierz **formantów blokady**.</span><span class="sxs-lookup"><span data-stu-id="38837-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38837-113">Blokowanie formantów uniemożliwia ich przeciąganie nowy rozmiar lub lokalizacji na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="38837-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="38837-114">Jednak nadal można zmienić rozmiar lub położenie kontrolki poprzez **właściwości** oknie lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="38837-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="38837-115">Aby zablokować wszystkie formanty w formularzu</span><span class="sxs-lookup"><span data-stu-id="38837-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="38837-116">Z **Format** menu, wybierz **formantów blokady**.</span><span class="sxs-lookup"><span data-stu-id="38837-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38837-117">To polecenie umożliwia zablokowanie rozmiar formularza, ponieważ kontrolki formularza.</span><span class="sxs-lookup"><span data-stu-id="38837-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="38837-118">Aby odblokować wszystkie zablokowane kontrolek w formularzu</span><span class="sxs-lookup"><span data-stu-id="38837-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="38837-119">Z **Format** menu, wybierz **formantów blokady**.</span><span class="sxs-lookup"><span data-stu-id="38837-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="38837-120">Wszystkie uprzednio zablokowaną kontrolki w formularzu są teraz odblokowane.</span><span class="sxs-lookup"><span data-stu-id="38837-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="38837-121">Aby odblokować zablokowany formantów indywidualnie</span><span class="sxs-lookup"><span data-stu-id="38837-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="38837-122">W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `false`.</span><span class="sxs-lookup"><span data-stu-id="38837-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="38837-123">(Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).</span><span class="sxs-lookup"><span data-stu-id="38837-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38837-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38837-124">See also</span></span>
- [<span data-ttu-id="38837-125">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38837-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
- [<span data-ttu-id="38837-126">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38837-126">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="38837-127">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="38837-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="38837-128">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38837-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="38837-129">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="38837-129">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
