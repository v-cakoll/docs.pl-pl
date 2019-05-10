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
ms.openlocfilehash: a2b9524b6a3e3c77d3c68c4d9e138b8c0e2a9373
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662286"
---
# <a name="how-to-render-a-visual-style-element"></a>Instrukcje: renderowanie elementu stylu wizualnego
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Przestrzeń nazw udostępnia <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> obiekty reprezentujące użytkownika Windows interfejsu (UI) elementy objęte stylów wizualnych. W tym temacie przedstawiono sposób użycia <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> klasy do renderowania <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> reprezentujący **Wyloguj** i **Shut Down** przyciski, menu Start.  
  
### <a name="to-render-a-visual-style-element"></a>Renderowanie elementu stylu wizualnego  
  
1. Utwórz <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> i ustaw ją na element, który chcemy narysować. Zwróć uwagę na użycie <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> Konstruktor spowoduje zgłoszenie wyjątku, jeśli style wizualne są wyłączone lub element jest niezdefiniowany.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. Wywołaj <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metodę, aby renderować element <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> obecnie reprezentuje.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Niestandardowy formant pochodzące z <xref:System.Windows.Forms.Control> klasy.  
  
- A <xref:System.Windows.Forms.Form> obsługujący kontrolki niestandardowej.  
  
- Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Renderowanie kontrolek przy użyciu stylów wizualnych](rendering-controls-with-visual-styles.md)
