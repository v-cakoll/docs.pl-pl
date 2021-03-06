---
title: 'Instrukcje: Wypełnianie kafelków w obrębie kształtu obrazem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: a906db44a548361df2822efa24d1dd1849cb5a24
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063737"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Instrukcje: Wypełnianie kafelków w obrębie kształtu obrazem
Zgodnie z kafelków mogą być umieszczane obok siebie na pokrycie piętra, prostokątne obrazy mogą być umieszczone obok siebie do wypełnienia kształtu (fragment). Na kafelku wewnątrz kształtu, użyj pędzla tekstury. Podczas konstruowania <xref:System.Drawing.TextureBrush> obiektu w Argumenty przekazane do konstruktora jest <xref:System.Drawing.Image> obiektu. Malowanie wnętrza kształtu przy użyciu pędzli tekstury, kształt zostanie wypełniony powtarzających się kopii tego obrazu.  
  
 Właściwość tryb zawijania <xref:System.Drawing.TextureBrush> obiektu określa, jak obraz, który jest ustawiony jako jest powtarzany w siatce kartezjańskiej. Można tworzyć Kafelki w siatce, że ten sam orientacji, czy też mają być obrazu przerzucić od położenia na siatce co do następnego. Przerzucanie może być poziome, pionowe lub obu. W poniższych przykładach pokazano fragmentacji z różnymi typami Przerzucanie.  
  
### <a name="to-tile-an-image"></a>Na kafelku obrazu  
  
- W tym przykładzie używa na poniższej ilustracji 75 x 75 do kafelka prostokąt 200 x 200.  
  
 ![Obraz Kafelek, który pokazuje czerwone dom i drzewa.](./media/how-to-tile-a-shape-with-an-image/rectangle-tile-200x200.gif)  
  
- Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przy użyciu obrazu. Należy pamiętać, że wszystkie Kafelki mają tę samą orientację; nie ma żadnych Przerzucanie.  
  
 ![Prostokąt układu sąsiadującego za pomocą obrazu przy użyciu tego samego orientacja dla wszystkich kafelków.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-no-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Aby przerzucić obraz w poziomie podczas fragmentacji  
  
- W tym przykładzie używa tego samego obrazu 75 x 75 do wypełnienia prostokąt 200 x 200. Tryb zawijania jest ustawiony na przerzucić obraz w poziomie. Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przy użyciu obrazu. Należy pamiętać, że po przeniesieniu z jednym kafelkiem dalej w danym wierszu obrazu jest odwrócony poziomo.  
  
 ![Prostokąt układu sąsiadującego za pomocą obrazu odwrócić w poziomie.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Aby przerzucić obraz w pionie podczas fragmentacji  
  
- W tym przykładzie używa tego samego obrazu 75 x 75 do wypełnienia prostokąt 200 x 200. Tryb zawijania jest ustawiony na Przerzuć obraz w pionie.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Aby przerzucić obraz w pionie i poziomie podczas fragmentacji  
  
- W tym przykładzie używa tego samego obrazu 75 x 75 do kafelka prostokąt 200 x 200. Tryb zawijania jest ustawiony na przerzucić obraz w poziomie i w pionie. Poniższa ilustracja przedstawia, jak prostokąta jest rozmieszczany przez obraz. Należy pamiętać, że po przeniesieniu z jednym kafelkiem dalej w danym wierszu obrazu jest odwrócony poziomo i jak przenieść z jednym kafelkiem dalej w danej kolumnie, obraz, który jest odwrócony w pionie.  
  
 ![Prostokąt układu sąsiadującego za pomocą obrazu odwrócić poziomo i pionowo.](./media/how-to-tile-a-shape-with-an-image/rectangle-tiled-image-horizontal-vertical-flip.gif)  
  
 [!code-csharp[System.Drawing.UsingABrush#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
