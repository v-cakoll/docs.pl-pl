---
title: 'Instrukcje: ustawienie maski wprowadzania'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 14591b313b0ba4fc2a0a30a45c693147f00050b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207548"
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="bf876-102">Instrukcje: ustawienie maski wprowadzania</span><span class="sxs-lookup"><span data-stu-id="bf876-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="bf876-103">Formant pola tekstowego maskowanego jest formant pola tekstowego rozszerzonego, który obsługuje składni deklaratywnej akceptowanie lub odrzucanie dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf876-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="bf876-104">Ustawiając właściwość maski, można określić danych wejściowych użytkownika dozwolony bez konieczności pisania wszelkie logikę niestandardowego sprawdzania poprawności w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf876-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="bf876-105">Aby uzyskać więcej informacji, zobacz sekcję Uwagi <xref:System.Windows.Forms.MaskedTextBox> klasy.</span><span class="sxs-lookup"><span data-stu-id="bf876-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="bf876-106">Właściwość maski ręcznie</span><span class="sxs-lookup"><span data-stu-id="bf876-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="bf876-107">Jeśli znasz znaki, które obsługuje właściwość maska, można go wprowadzić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="bf876-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="bf876-108">Podsumowanie znaków, które obsługuje właściwość maska, zobacz sekcję Uwagi <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf876-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="bf876-109">Aby ręcznie ustawić właściwość maski</span><span class="sxs-lookup"><span data-stu-id="bf876-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="bf876-110">W **projektowania** widoku, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="bf876-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="bf876-111">W **właściwości** oknie Znajdź <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf876-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="bf876-112">Wpisz maskę, który ma.</span><span class="sxs-lookup"><span data-stu-id="bf876-112">Type the mask that you want.</span></span> <span data-ttu-id="bf876-113">Na przykład wpisz `###`.</span><span class="sxs-lookup"><span data-stu-id="bf876-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="bf876-114">Za pomocą okna dialogowego maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="bf876-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="bf876-115">Maska wprowadzania, okno dialogowe zawiera kilka wstępnie zdefiniowanych maski wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="bf876-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="bf876-116">Można również zmienić maski wstępnie zdefiniowanych lub ręcznie wprowadź własne maski.</span><span class="sxs-lookup"><span data-stu-id="bf876-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="bf876-117">Aby otworzyć okno dialogowe maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="bf876-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="bf876-118">W **projektowania** widoku, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="bf876-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="bf876-119">Kliknij tag, aby otworzyć **zadania MaskedTextBox** panelu.</span><span class="sxs-lookup"><span data-stu-id="bf876-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="bf876-120">Kliknij przycisk **ustawienie maski**.</span><span class="sxs-lookup"><span data-stu-id="bf876-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="bf876-121">\- lub —</span><span class="sxs-lookup"><span data-stu-id="bf876-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="bf876-122">W **właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf876-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="bf876-123">Kliknij przycisk wielokropka w kolumnie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf876-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="bf876-124">**Maska wprowadzania** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="bf876-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="bf876-125">Aby użyć okna dialogowego maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="bf876-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="bf876-126">(Opcjonalnie) Kliknij jeden z wstępnie zdefiniowanych masek na liście.</span><span class="sxs-lookup"><span data-stu-id="bf876-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="bf876-127">(Opcjonalnie) Wstępnie zdefiniowane maska w edycji **maski** pole.</span><span class="sxs-lookup"><span data-stu-id="bf876-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="bf876-128">(Opcjonalnie) Wpisz nową maskę w **maski** pole.</span><span class="sxs-lookup"><span data-stu-id="bf876-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="bf876-129">Oznacza to nie trzeba użyć jednego z wstępnie zdefiniowanych maski.</span><span class="sxs-lookup"><span data-stu-id="bf876-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bf876-130">Okno (wersja zapoznawcza) zawiera znaki, które użytkownik będzie widział w <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="bf876-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="bf876-131">Te znaki znajdują się wskazówki pomagające użytkownik może wprowadzić poprawne dane.</span><span class="sxs-lookup"><span data-stu-id="bf876-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="bf876-132">Zaznacz lub wyczyść **ValidatingType użyj** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="bf876-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="bf876-133">**ValidatingType użyj** pole wyboru określa, czy typ danych służy do Sprawdź danych wejściowych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf876-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="bf876-134">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bf876-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="bf876-135">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf876-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="bf876-136">Maska jest wprowadzana w **maski** właściwość **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="bf876-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf876-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf876-137">See also</span></span>

- [<span data-ttu-id="bf876-138">Przewodnik: praca z kontrolką MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="bf876-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
