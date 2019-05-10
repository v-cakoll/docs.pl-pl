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
ms.openlocfilehash: 3fbaaae53aa60f6356c3a8daa0513de86ef2dacb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211297"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="5eda3-102">Instrukcje: Stosowanie modyfikatorów i właściwości „GenerateMember"</span><span class="sxs-lookup"><span data-stu-id="5eda3-102">How to: Use the Modifiers and GenerateMember Properties</span></span>

<span data-ttu-id="5eda3-103">Po umieszczeniu składnika w formularzu Windows dwie właściwości są dostarczane przez środowisko projektowania: `GenerateMember` i `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="5eda3-104">`GenerateMember` Właściwość określa, kiedy Windows Forms Designer generuje zmienną składową dla składnika.</span><span class="sxs-lookup"><span data-stu-id="5eda3-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="5eda3-105">`Modifiers` Właściwość jest modyfikator dostępu przypisane do tej zmiennej elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5eda3-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="5eda3-106">Jeśli wartość `GenerateMember` właściwość `false`, wartość `Modifiers` właściwość nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="5eda3-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>

## <a name="specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="5eda3-107">Określ, czy składnik jest elementem członkowskim formularza</span><span class="sxs-lookup"><span data-stu-id="5eda3-107">Specify whether a component is a member of the form</span></span>

1. <span data-ttu-id="5eda3-108">W programie Windows Forms Designer w programie Visual Studio Otwórz formularz.</span><span class="sxs-lookup"><span data-stu-id="5eda3-108">In Visual Studio, in the Windows Forms Designer, open your form.</span></span>

2. <span data-ttu-id="5eda3-109">Otwórz **przybornika**i w formularzu, należy umieścić trzy <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="5eda3-109">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>

3. <span data-ttu-id="5eda3-110">Ustaw `GenerateMember` i `Modifiers` właściwości dla każdego <xref:System.Windows.Forms.Button> kontroli zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="5eda3-110">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>

    |<span data-ttu-id="5eda3-111">Nazwa przycisku</span><span class="sxs-lookup"><span data-stu-id="5eda3-111">Button name</span></span>|<span data-ttu-id="5eda3-112">Wartość GenerateMember</span><span class="sxs-lookup"><span data-stu-id="5eda3-112">GenerateMember value</span></span>|<span data-ttu-id="5eda3-113">Wartość modyfikatorów</span><span class="sxs-lookup"><span data-stu-id="5eda3-113">Modifiers value</span></span>|
    |-----------------|--------------------------|---------------------|
    |`button1`|`true`|`private`|
    |`button2`|`true`|`protected`|
    |`button3`|`false`|<span data-ttu-id="5eda3-114">Nie wprowadzono zmian</span><span class="sxs-lookup"><span data-stu-id="5eda3-114">No change</span></span>|

4. <span data-ttu-id="5eda3-115">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="5eda3-115">Build the solution.</span></span>

5. <span data-ttu-id="5eda3-116">W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5eda3-116">In **Solution Explorer**, click the **Show All Files** button.</span></span>

6. <span data-ttu-id="5eda3-117">Otwórz **Form1** węzła, a następnie w **Edytor kodu**, otwórz **Form1.Designer.vb** lub **Form1.Designer.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="5eda3-117">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="5eda3-118">Ten plik zawiera kod wyemitowane przez Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="5eda3-118">This file contains the code emitted by the Windows Forms Designer.</span></span>

7. <span data-ttu-id="5eda3-119">Znajdź deklaracje dla trzech przycisków.</span><span class="sxs-lookup"><span data-stu-id="5eda3-119">Find the declarations for the three buttons.</span></span> <span data-ttu-id="5eda3-120">Poniższy przykład kodu pokazuje różnice określony przez `GenerateMember` i `Modifiers` właściwości.</span><span class="sxs-lookup"><span data-stu-id="5eda3-120">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>

     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]

     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]

> [!NOTE]
> <span data-ttu-id="5eda3-121">Domyślnie Windows Forms Designer przypisuje `private` (`Friend` w języku Visual Basic) modyfikatora kontenera formanty, takie jak <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="5eda3-121">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="5eda3-122">Jeśli podstawa <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Form> zawiera formant kontenera nie będzie akceptować nowych elementów podrzędnych formularzy i kontrolek dziedziczone.</span><span class="sxs-lookup"><span data-stu-id="5eda3-122">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="5eda3-123">Rozwiązaniem jest zmiana modyfikator kontrolki podstawowym kontenerem na `protected` lub `public`.</span><span class="sxs-lookup"><span data-stu-id="5eda3-123">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eda3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5eda3-124">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="5eda3-125">Formularze Windows Forms — dziedziczenie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="5eda3-125">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="5eda3-126">Przewodnik: Demonstrowanie dziedziczenia wizualizacji</span><span class="sxs-lookup"><span data-stu-id="5eda3-126">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)
- [<span data-ttu-id="5eda3-127">Instrukcje: Dziedziczenie formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="5eda3-127">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
