---
title: 'Porady: blokowanie formantów do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: f05da53f134f13bf5edbbe7ab8c5973f79bbca4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="8f0a4-102">Porady: blokowanie formantów do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8f0a4-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="8f0a4-103">Podczas projektowania interfejsu użytkownika (UI) aplikacji systemu Windows, można zablokować formantów po znajdują się one poprawnie, tak aby nie mogą przypadkowo przenieść lub zmienić ich rozmiar przy ustawianiu inne właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="8f0a4-104">Ponadto można zablokować i odblokować wszystkich kontrolek w formularzu jednocześnie, co jest przydatne w przypadku wielu formantów, lub można odblokować pojedynczych formantów.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="8f0a4-105">Po umieszczeniu wszystkich kontrolek żądanym na formularzu, należy zablokować je w miejscu, aby zapobiec błędnej przepływu.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f0a4-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8f0a4-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8f0a4-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8f0a4-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="8f0a4-109">Aby zablokować formantu</span><span class="sxs-lookup"><span data-stu-id="8f0a4-109">To lock a control</span></span>  
  
1.  <span data-ttu-id="8f0a4-110">W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz `true`.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="8f0a4-111">(Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).</span><span class="sxs-lookup"><span data-stu-id="8f0a4-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="8f0a4-112">Alternatywnie kliknij formant prawym przyciskiem myszy i wybierz polecenie **formanty blokady**.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f0a4-113">Blokowanie formantów zapobiega ich przeciąganie do nowego rozmiaru lub lokalizacji na powierzchni projektu.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="8f0a4-114">Jednak nadal zmianą rozmiaru lub lokalizacji formantów za pomocą klasy **właściwości** okna lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="8f0a4-115">Aby zablokować wszystkich kontrolek w formularzu</span><span class="sxs-lookup"><span data-stu-id="8f0a4-115">To lock all the controls on a form</span></span>  
  
1.  <span data-ttu-id="8f0a4-116">Z **Format** menu, wybierz **formanty blokady**.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f0a4-117">To polecenie blokuje również rozmiar formularza, ponieważ formularz jest formantem.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="8f0a4-118">Aby odblokować wszystkie zablokowane formantów w formularzu</span><span class="sxs-lookup"><span data-stu-id="8f0a4-118">To unlock all locked controls on a form</span></span>  
  
1.  <span data-ttu-id="8f0a4-119">Z **Format** menu, wybierz **formanty blokady**.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="8f0a4-120">Wszystkie poprzednio zablokowanymi kontrolek w formularzu są teraz odblokowane.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="8f0a4-121">Aby odblokować formanty zablokowane indywidualnie</span><span class="sxs-lookup"><span data-stu-id="8f0a4-121">To unlock locked controls individually</span></span>  
  
1.  <span data-ttu-id="8f0a4-122">W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz `false`.</span><span class="sxs-lookup"><span data-stu-id="8f0a4-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="8f0a4-123">(Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).</span><span class="sxs-lookup"><span data-stu-id="8f0a4-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0a4-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f0a4-124">See Also</span></span>  
 [<span data-ttu-id="8f0a4-125">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f0a4-125">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="8f0a4-126">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f0a4-126">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="8f0a4-127">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="8f0a4-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="8f0a4-128">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f0a4-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="8f0a4-129">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="8f0a4-129">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
