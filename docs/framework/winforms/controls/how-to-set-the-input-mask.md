---
title: 'Porady: ustawienie maski wprowadzania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a><span data-ttu-id="8cbc3-102">Porady: ustawienie maski wprowadzania</span><span class="sxs-lookup"><span data-stu-id="8cbc3-102">How to: Set the Input Mask</span></span>
<span data-ttu-id="8cbc3-103">Kontrolki pola tekstowego maskowanego jest rozszerzony polu tekstowym obsługująca składni deklaratywnej akceptowanie lub odrzucanie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-103">The masked text box control is an enhanced text box control that supports a declarative syntax for accepting or rejecting user input.</span></span> <span data-ttu-id="8cbc3-104">Przez ustawienie właściwości maski, można określić danych wejściowych użytkownika dopuszczalny bez pisania wszelka logika niestandardowego sprawdzania poprawności w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-104">By setting the Mask property, you can specify the allowable user input without writing any custom validation logic in your application.</span></span> <span data-ttu-id="8cbc3-105">Aby uzyskać więcej informacji, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox> klasy.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-105">For more information, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox> class.</span></span>  
  
## <a name="setting-the-mask-property-manually"></a><span data-ttu-id="8cbc3-106">Ustawienie właściwości maski ręcznie</span><span class="sxs-lookup"><span data-stu-id="8cbc3-106">Setting the Mask Property Manually</span></span>  
 <span data-ttu-id="8cbc3-107">Jeśli znasz znaki, które obsługuje właściwość maska, można go wprowadzić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-107">If you are familiar with the characters that the Mask property supports, you can enter it manually.</span></span> <span data-ttu-id="8cbc3-108">Podsumowanie znaki, które obsługuje właściwość maska, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-108">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
#### <a name="to-set-the-mask-property-manually"></a><span data-ttu-id="8cbc3-109">Aby ręcznie ustawić właściwość maska</span><span class="sxs-lookup"><span data-stu-id="8cbc3-109">To set the Mask property manually</span></span>  
  
1.  <span data-ttu-id="8cbc3-110">W **projekt** widok, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-110">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
2.  <span data-ttu-id="8cbc3-111">W **właściwości** okna, zlokalizuj <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-111">In the **Properties** window, locate the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
3.  <span data-ttu-id="8cbc3-112">Wpisz maskę, który ma.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-112">Type the mask that you want.</span></span> <span data-ttu-id="8cbc3-113">Na przykład wpisz `###`.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-113">For example, type `###`.</span></span>  
  
## <a name="using-the-input-mask-dialog-box"></a><span data-ttu-id="8cbc3-114">Za pomocą okna dialogowego maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="8cbc3-114">Using the Input Mask Dialog Box</span></span>  
 <span data-ttu-id="8cbc3-115">Okno dialogowe maska wprowadzania zawiera kilka wstępnie zdefiniowanych maski wprowadzania.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-115">The Input Mask dialog box provides some predefined input masks.</span></span> <span data-ttu-id="8cbc3-116">Można również zmienić maski wstępnie zdefiniowanych lub ręcznie wprowadź własne maski.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-116">You can also change the predefined masks or enter your own mask manually.</span></span>  
  
#### <a name="to-open-the-input-mask-dialog-box"></a><span data-ttu-id="8cbc3-117">Aby otworzyć okno dialogowe maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="8cbc3-117">To open the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="8cbc3-118">W **projekt** widok, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-118">In **Design** view, select a <xref:System.Windows.Forms.MaskedTextBox>.</span></span>  
  
    1.  <span data-ttu-id="8cbc3-119">Kliknij tag, aby otworzyć **zadania MaskedTextBox** panelu.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-119">Click the smart tag to open the **MaskedTextBox Tasks** panel.</span></span>  
  
    2.  <span data-ttu-id="8cbc3-120">Kliknij przycisk **ustawić maski**.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-120">Click **Set Mask**.</span></span>  
  
     <span data-ttu-id="8cbc3-121">\-lub -</span><span class="sxs-lookup"><span data-stu-id="8cbc3-121">\- or -</span></span>  
  
    1.  <span data-ttu-id="8cbc3-122">W **właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-122">In the **Properties** window, select the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
    2.  <span data-ttu-id="8cbc3-123">Kliknij przycisk wielokropka w kolumnie wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-123">Click the ellipsis button in the property value column.</span></span>  
  
     <span data-ttu-id="8cbc3-124">**Maska wprowadzania** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-124">The **Input Mask** dialog box appears.</span></span>  
  
#### <a name="to-use-the-input-mask-dialog-box"></a><span data-ttu-id="8cbc3-125">Aby użyć okna dialogowego maska wprowadzania</span><span class="sxs-lookup"><span data-stu-id="8cbc3-125">To use the Input Mask dialog box</span></span>  
  
1.  <span data-ttu-id="8cbc3-126">(Opcjonalnie) Kliknij jeden z wstępnie zdefiniowanych masek na liście.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-126">(Optional) Click one of the predefined masks in the list.</span></span>  
  
2.  <span data-ttu-id="8cbc3-127">(Opcjonalnie) Edytuj maski wstępnie zdefiniowanych w **maski** pole.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-127">(Optional) Edit the predefined mask in the **Mask** box.</span></span>  
  
3.  <span data-ttu-id="8cbc3-128">(Opcjonalnie) Wpisz nową maskę w **maski** pole.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-128">(Optional) Type a new mask in the **Mask** box.</span></span> <span data-ttu-id="8cbc3-129">Oznacza to nie trzeba użyć jednej z wstępnie zdefiniowanych maski.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-129">That is, you do not have to use one of the predefined masks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8cbc3-130">Pole podglądu zawiera znaki, które użytkownik będzie widział w <xref:System.Windows.Forms.MaskedTextBox>.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-130">The Preview box displays the characters that the user sees in the <xref:System.Windows.Forms.MaskedTextBox>.</span></span> <span data-ttu-id="8cbc3-131">Te znaki są także przewodnik ułatwiający użytkownik może wprowadzić dane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-131">These characters are a guide to help the user enter the data correctly.</span></span>  
  
4.  <span data-ttu-id="8cbc3-132">Wybierz lub wyczyść **ValidatingType użyj** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-132">Select or clear the **Use ValidatingType** check box.</span></span> <span data-ttu-id="8cbc3-133">**ValidatingType użyj** pole wyboru określa, czy typ danych jest używana do Sprawdź wprowadzania danych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-133">The **Use ValidatingType** check box specifies whether a data type is used to verify the data input by the user.</span></span> <span data-ttu-id="8cbc3-134">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-134">For more information, see the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property.</span></span>  
  
5.  <span data-ttu-id="8cbc3-135">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-135">Click **OK**.</span></span>  
  
     <span data-ttu-id="8cbc3-136">Maska została wprowadzona w **maski** właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="8cbc3-136">The mask is entered in the **Mask** property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbc3-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cbc3-137">See Also</span></span>  
 [<span data-ttu-id="8cbc3-138">Wskazówki: Praca z formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="8cbc3-138">Walkthrough: Working with the MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
