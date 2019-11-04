---
title: 'Porady: blokowanie formantów do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d157ddc8be4b5fa0057241b562e76b566e8dad99
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458341"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="e1ff5-102">Instrukcje: blokowanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1ff5-102">How to: Lock controls to Windows Forms</span></span>

<span data-ttu-id="e1ff5-103">Podczas projektowania interfejsu użytkownika aplikacji systemu Windows, można zablokować kontrolki po ich poprawnym umieszczeniu, aby nie przełączać ani zmieniać ich rozmiaru podczas ustawiania innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

<span data-ttu-id="e1ff5-104">Ponadto można zablokować i odblokować wszystkie kontrolki w formularzu jednocześnie, co jest przydatne w przypadku formularzy z wieloma kontrolkami lub można odblokować poszczególne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="e1ff5-105">Po umieszczeniu wszystkich kontrolek, w których chcesz, Zablokuj je wszystkie w miejscu, aby uniknąć błędnego przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="e1ff5-106">Aby zablokować kontrolkę</span><span class="sxs-lookup"><span data-stu-id="e1ff5-106">To lock a control</span></span>

<span data-ttu-id="e1ff5-107">W oknie **Właściwości** programu Visual Studio wybierz właściwość **zablokowana** , a następnie wybierz pozycję **prawda**.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-107">In the **Properties** window of Visual Studio, select the **Locked** property and then select **true**.</span></span> <span data-ttu-id="e1ff5-108">(Dwukrotne kliknięcie nazwy powoduje przełączenie ustawienia właściwości.)</span><span class="sxs-lookup"><span data-stu-id="e1ff5-108">(Double-clicking the name toggles the property setting.)</span></span>

<span data-ttu-id="e1ff5-109">Alternatywnie kliknij prawym przyciskiem myszy formant i wybierz polecenie **Zablokuj kontrolki**.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="e1ff5-110">Kontrolki blokowania uniemożliwiają przeciągnięcie ich do nowego rozmiaru lub lokalizacji na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="e1ff5-111">Jednak nadal można zmienić rozmiar lub lokalizację kontrolek za pomocą okna **Właściwości** lub kodu.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="e1ff5-112">Aby zablokować wszystkie kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="e1ff5-112">To lock all the controls on a form</span></span>

<span data-ttu-id="e1ff5-113">Z menu **Format** wybierz opcję **Zablokuj kontrolki**.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-113">From the **Format** menu, choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="e1ff5-114">To polecenie blokuje również rozmiar formularza, ponieważ formularz jest formantem.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="e1ff5-115">Aby odblokować wszystkie zablokowane kontrolki w formularzu</span><span class="sxs-lookup"><span data-stu-id="e1ff5-115">To unlock all locked controls on a form</span></span>

<span data-ttu-id="e1ff5-116">Z menu **Format** wybierz opcję **Zablokuj kontrolki**.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-116">From the **Format** menu, choose **Lock Controls**.</span></span>

<span data-ttu-id="e1ff5-117">Wszystkie poprzednio zablokowane kontrolki w formularzu są teraz odblokowane.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="e1ff5-118">Aby odblokować zablokowane kontrolki indywidualnie</span><span class="sxs-lookup"><span data-stu-id="e1ff5-118">To unlock locked controls individually</span></span>

<span data-ttu-id="e1ff5-119">W oknie **Właściwości** wybierz **zablokowaną** właściwość, a następnie wybierz **wartość FAŁSZ**.</span><span class="sxs-lookup"><span data-stu-id="e1ff5-119">In the **Properties** window, select the **Locked** property and then select **false**.</span></span> <span data-ttu-id="e1ff5-120">(Dwukrotne kliknięcie nazwy powoduje przełączenie ustawienia właściwości.)</span><span class="sxs-lookup"><span data-stu-id="e1ff5-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="e1ff5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1ff5-121">See also</span></span>

- [<span data-ttu-id="e1ff5-122">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1ff5-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="e1ff5-123">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="e1ff5-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="e1ff5-124">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1ff5-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="e1ff5-125">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="e1ff5-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
