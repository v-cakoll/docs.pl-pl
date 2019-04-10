---
title: 'Instrukcje: renderowanie elementu stylu wizualnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 57c2bc5722f77338225d70b514345344211656dc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312400"
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="340bd-102">Instrukcje: renderowanie elementu stylu wizualnego</span><span class="sxs-lookup"><span data-stu-id="340bd-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="340bd-103"><xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Przestrzeń nazw udostępnia <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> obiekty reprezentujące użytkownika Windows interfejsu (UI) elementy objęte stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="340bd-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="340bd-104">W tym temacie przedstawiono sposób użycia <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> klasy do renderowania <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> reprezentujący **Wyloguj** i **Shut Down** przyciski, menu Start.</span><span class="sxs-lookup"><span data-stu-id="340bd-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="340bd-105">Renderowanie elementu stylu wizualnego</span><span class="sxs-lookup"><span data-stu-id="340bd-105">To render a visual style element</span></span>  
  
1. <span data-ttu-id="340bd-106">Utwórz <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> i ustaw ją na element, który chcemy narysować.</span><span class="sxs-lookup"><span data-stu-id="340bd-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="340bd-107">Zwróć uwagę na użycie <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> Konstruktor spowoduje zgłoszenie wyjątku, jeśli style wizualne są wyłączone lub element jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="340bd-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. <span data-ttu-id="340bd-108">Wywołaj <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metodę, aby renderować element <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> obecnie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="340bd-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="340bd-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="340bd-109">Compiling the Code</span></span>  
 <span data-ttu-id="340bd-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="340bd-110">This example requires:</span></span>  
  
-   <span data-ttu-id="340bd-111">Niestandardowy formant pochodzące z <xref:System.Windows.Forms.Control> klasy.</span><span class="sxs-lookup"><span data-stu-id="340bd-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="340bd-112">A <xref:System.Windows.Forms.Form> obsługujący kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="340bd-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="340bd-113">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="340bd-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340bd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="340bd-114">See also</span></span>

- [<span data-ttu-id="340bd-115">Renderowanie formantów przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="340bd-115">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)
