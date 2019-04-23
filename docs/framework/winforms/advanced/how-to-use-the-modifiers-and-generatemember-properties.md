---
title: 'Instrukcje: Stosowanie modyfikatorów i właściwości „GenerateMember"'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 6194ef288bd43267c2b00fa6d7c6250e90b37c75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322644"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="6f30d-102">Instrukcje: Stosowanie modyfikatorów i właściwości „GenerateMember"</span><span class="sxs-lookup"><span data-stu-id="6f30d-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="6f30d-103">Po umieszczeniu składnika w formularzu Windows dwie właściwości są dostarczane przez środowisko projektowania: `GenerateMember` i `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="6f30d-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="6f30d-104">`GenerateMember` Właściwość określa, kiedy Windows Forms Designer generuje zmienną składową dla składnika.</span><span class="sxs-lookup"><span data-stu-id="6f30d-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="6f30d-105">`Modifiers` Właściwość jest modyfikator dostępu przypisane do tej zmiennej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6f30d-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="6f30d-106">Jeśli wartość `GenerateMember` właściwość `false`, wartość `Modifiers` właściwość nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="6f30d-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f30d-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="6f30d-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6f30d-108">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="6f30d-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6f30d-109">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="6f30d-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="6f30d-110">Aby określić, czy składnik jest elementem członkowskim formularza</span><span class="sxs-lookup"><span data-stu-id="6f30d-110">To specify whether a component is a member of the form</span></span>  
  
1. <span data-ttu-id="6f30d-111">Otwórz formularz Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="6f30d-111">In the Windows Forms Designer, open your form.</span></span>  
  
2. <span data-ttu-id="6f30d-112">Otwórz **przybornika**i w formularzu, należy umieścić trzy <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6f30d-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3. <span data-ttu-id="6f30d-113">Ustaw `GenerateMember` i `Modifiers` właściwości dla każdego <xref:System.Windows.Forms.Button> kontroli zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="6f30d-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="6f30d-114">Nazwa przycisku</span><span class="sxs-lookup"><span data-stu-id="6f30d-114">Button name</span></span>|<span data-ttu-id="6f30d-115">Wartość GenerateMember</span><span class="sxs-lookup"><span data-stu-id="6f30d-115">GenerateMember value</span></span>|<span data-ttu-id="6f30d-116">Wartość modyfikatorów</span><span class="sxs-lookup"><span data-stu-id="6f30d-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="6f30d-117">Nie wprowadzono zmian</span><span class="sxs-lookup"><span data-stu-id="6f30d-117">No change</span></span>|  
  
4. <span data-ttu-id="6f30d-118">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6f30d-118">Build the solution.</span></span>  
  
5. <span data-ttu-id="6f30d-119">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="6f30d-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6. <span data-ttu-id="6f30d-120">Otwórz **Form1** węzła, a następnie w **Edytor kodu**, otwórz **Form1.Designer.vb** lub **Form1.Designer.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="6f30d-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="6f30d-121">Ten plik zawiera kod wyemitowane przez Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="6f30d-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7. <span data-ttu-id="6f30d-122">Znajdź deklaracje dla trzech przycisków.</span><span class="sxs-lookup"><span data-stu-id="6f30d-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="6f30d-123">Poniższy przykład kodu pokazuje różnice określony przez `GenerateMember` i `Modifiers` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f30d-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="6f30d-124">Domyślnie Windows Forms Designer przypisuje `private` (`Friend` w języku Visual Basic) modyfikatora kontenera formanty, takie jak <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="6f30d-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="6f30d-125">Jeśli podstawa <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Form> zawiera formant kontenera nie będzie akceptować nowych elementów podrzędnych formularzy i kontrolek dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="6f30d-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="6f30d-126">Rozwiązaniem jest zmiana modyfikator kontrolki podstawowym kontenerem na `protected` lub `public`.</span><span class="sxs-lookup"><span data-stu-id="6f30d-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f30d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f30d-127">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="6f30d-128">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="6f30d-128">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="6f30d-129">Przewodnik: Demonstrowanie dziedziczenia wizualizacji</span><span class="sxs-lookup"><span data-stu-id="6f30d-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)
- [<span data-ttu-id="6f30d-130">Instrukcje: Dziedziczenie formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="6f30d-130">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
