---
title: 'Instrukcje: ustawienie maski wprowadzania'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949150"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="573d0-102">Instrukcje: ustawienie maski wprowadzania</span><span class="sxs-lookup"><span data-stu-id="573d0-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="573d0-103">Formant pole tekstowe z maską jest ulepszoną kontrolką pola tekstowego, która obsługuje deklaratywną składnię akceptowania lub odrzucania danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="573d0-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="573d0-104">Ustawiając właściwość mask, można określić dozwolone dane wejściowe użytkownika bez pisania niestandardowej logiki walidacji w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="573d0-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="573d0-105">Aby uzyskać więcej informacji, zobacz sekcję <xref:System.Windows.Forms.MaskedTextBox> uwagi klasy.</span><span class="sxs-lookup"><span data-stu-id="573d0-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="573d0-106">Ręczne ustawianie właściwości maski</span><span class="sxs-lookup"><span data-stu-id="573d0-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="573d0-107">Jeśli znasz znaki obsługiwane przez właściwość maski, możesz wprowadzić ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="573d0-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="573d0-108">Aby uzyskać podsumowanie znaków obsługiwanych przez właściwość maski, zobacz sekcję <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> uwagi właściwości.</span><span class="sxs-lookup"><span data-stu-id="573d0-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="573d0-109">Aby ustawić właściwość maski ręcznie</span><span class="sxs-lookup"><span data-stu-id="573d0-109">To set the Mask property manually</span></span>  
  
1. <span data-ttu-id="573d0-110">W widoku **projekt** wybierz pozycję a <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="573d0-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2. <span data-ttu-id="573d0-111">W oknie **Właściwości** Znajdź <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="573d0-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3. <span data-ttu-id="573d0-112">Wpisz żądaną maskę.</span><span class="sxs-lookup"><span data-stu-id="573d0-112">Type the mask that you want.</span></span> <span data-ttu-id="573d0-113">Na przykład wpisz `###`.</span><span class="sxs-lookup"><span data-stu-id="573d0-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="573d0-114">Korzystanie z okna dialogowego Maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="573d0-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="573d0-115">Okno dialogowe Maska wprowadzania zawiera kilka wstępnie zdefiniowanych masek wejściowych.</span><span class="sxs-lookup"><span data-stu-id="573d0-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="573d0-116">Możesz również zmienić wstępnie zdefiniowane maski lub ręcznie wprowadzić własną maskę.</span><span class="sxs-lookup"><span data-stu-id="573d0-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="573d0-117">Aby otworzyć okno dialogowe Maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="573d0-117">To open the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="573d0-118">W widoku **projekt** wybierz pozycję a <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="573d0-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1. <span data-ttu-id="573d0-119">Kliknij tag inteligentny, aby otworzyć panel **zadania formantem MaskedTextBox** .</span><span class="sxs-lookup"><span data-stu-id="573d0-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2. <span data-ttu-id="573d0-120">Kliknij pozycję **Ustaw maskę**.</span><span class="sxs-lookup"><span data-stu-id="573d0-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="573d0-121">\- lub —</span><span class="sxs-lookup"><span data-stu-id="573d0-121">\- or -</span></span>  
  
    1. <span data-ttu-id="573d0-122">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="573d0-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2. <span data-ttu-id="573d0-123">Kliknij przycisk wielokropka w kolumnie wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="573d0-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="573d0-124">Zostanie wyświetlone okno dialogowe **Maska wprowadzania** .</span><span class="sxs-lookup"><span data-stu-id="573d0-124">The **Input Mask** dialog box appears.</span></span>  
  
### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="573d0-125">Aby użyć okna dialogowego Maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="573d0-125">To use the Input Mask dialog box</span></span>  
  
1. <span data-ttu-id="573d0-126">Obowiązkowe Kliknij jedną ze wstępnie zdefiniowanych masek na liście.</span><span class="sxs-lookup"><span data-stu-id="573d0-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2. <span data-ttu-id="573d0-127">Obowiązkowe Edytuj wstępnie zdefiniowaną maskę w polu **maska** .</span><span class="sxs-lookup"><span data-stu-id="573d0-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3. <span data-ttu-id="573d0-128">Obowiązkowe W polu **maska** wpisz nową maskę.</span><span class="sxs-lookup"><span data-stu-id="573d0-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="573d0-129">Oznacza to, że nie trzeba używać jednej ze wstępnie zdefiniowanych masek.</span><span class="sxs-lookup"><span data-stu-id="573d0-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="573d0-130">W polu Podgląd wyświetlane są znaki, które użytkownik widzi w <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="573d0-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="573d0-131">Te znaki to przewodnik ułatwiający prawidłowe wprowadzanie danych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="573d0-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4. <span data-ttu-id="573d0-132">Zaznacz lub wyczyść pole wyboru **Użyj walidacji** .</span><span class="sxs-lookup"><span data-stu-id="573d0-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="573d0-133">Pole wyboru **Użyj walidacji** określa, czy typ danych jest używany do weryfikowania danych wejściowych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="573d0-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="573d0-134">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="573d0-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5. <span data-ttu-id="573d0-135">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="573d0-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="573d0-136">Maska jest wprowadzana we właściwości **Mask** w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="573d0-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573d0-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="573d0-137">See also</span></span>

- [<span data-ttu-id="573d0-138">Przewodnik: Praca z kontrolką formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="573d0-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
