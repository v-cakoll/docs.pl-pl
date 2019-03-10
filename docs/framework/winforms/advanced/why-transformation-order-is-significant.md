---
title: Dlaczego kolejność przekształcania jest ważna
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], order significance
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
ms.openlocfilehash: 4a65e588984241affea3083810b4901266480ea4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710397"
---
# <a name="why-transformation-order-is-significant"></a>Dlaczego kolejność przekształcania jest ważna
Pojedynczy <xref:System.Drawing.Drawing2D.Matrix> obiektu można przechowywać w jednej transformacji lub sekwencja przekształceń. Drugim jest nazywany złożonych transformacji. Macierzy transformacji złożonego mnożąc macierzy transformacji indywidualnych.  
  
## <a name="composite-transform-examples"></a>Przykłady złożone przekształcenia  
 W złożonych transformacji ważne jest kolejność pojedyncze przekształcenia. Na przykład jeśli najpierw obrócić, a następnie skalować, tłumaczenie, uzyskujesz różne wyniki niż w przypadku najpierw tłumaczenia, obracanie, następnie skalowanie. W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], composite — przekształcenia są zbudowane od lewej do prawej. Jeśli S, R i T są odpowiednio macierzy skalowania, obrotu i tłumaczenia, następnie produktu SRT (w tej kolejności) jest macierzy transformacji złożonego, pierwszy skalowana, obraca się, a następnie dokonuje translacji. Macierz produkowane przez produkt SRT różni się od macierzy produkowane przez produkt TR, Technical Router.  
  
 Jedną z przyczyn których kolejność ma znaczenie jest, że transformacji, takie jak obrotu i skalowania są wykonywane względem współrzędnych punktu początkowego. Skalowanie obiektu, który skupia się na źródło daje różne wyniki niż skalowanie obiekt, który został przeniesiony poza pochodzenia. Podobnie Obracanie obiektu, który skupia się na źródło daje różne wyniki niż Obracanie obiektu, który został przeniesiony poza pochodzenia.  
  
 Poniższy przykład łączy skalowania, obrotu i tłumaczenia (w tej kolejności) w celu utworzenia złożonego transformacji. Argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> przekazany do <xref:System.Drawing.Graphics.RotateTransform%2A> metoda wskazuje, że obrót przeprowadzić skalowanie. Podobnie, argument <xref:System.Drawing.Drawing2D.MatrixOrder.Append> przekazany do <xref:System.Drawing.Graphics.TranslateTransform%2A> metoda wskazuje wykonać tłumaczenie obrót. <xref:System.Drawing.Drawing2D.MatrixOrder.Append> i <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend> są elementami członkowskimi <xref:System.Drawing.Drawing2D.MatrixOrder> wyliczenia.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 Poniższy przykład wykonuje ten sam wywołania metody, jak w poprzednim przykładzie, ale kolejność wywołań została odwrócona. Wynikowy kolejność operacji jest najpierw tłumaczenia, obracanie, a następnie skalę, co daje wynik bardzo różnią się od pierwszej skali, następnie obracać, a następnie tłumaczenie.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 Jednym ze sposobów, aby odwrócić porządek pojedyncze przekształcenia w złożonych transformacji jest odwrócić kolejność sekwencji wywołania metody. Drugi sposób, aby kontrolować kolejność operacji jest zmiana argumentu order w macierzy. Poniższy przykład jest taki sam, jak w poprzednim przykładzie, chyba że <xref:System.Drawing.Drawing2D.MatrixOrder.Append> został zmieniony na <xref:System.Drawing.Drawing2D.MatrixOrder.Prepend>. Mnożenie macierzy jest wykonywane w kolejności SRT, w których macierzy skalowanie S, R i T, obracać i tłumaczenie, odpowiednio. Kolejność złożonych transformacji jest najpierw skalować, obracanie, a następnie tłumaczenie.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 Wynik natychmiast poprzedni przykład jest taka sama jak wynik pierwszego przykładu w tym temacie. To dlatego firma Microsoft odwrócenie kolejności wywołań metod i kolejność mnożenie macierzy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Drawing2D.Matrix>
- [Systemy i przekształcenia współrzędnych](coordinate-systems-and-transformations.md)
- [Używanie przekształceń w zarządzanym GDI+](using-transformations-in-managed-gdi.md)
