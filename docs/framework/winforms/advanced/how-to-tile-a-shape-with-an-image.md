---
title: "Porady: wypełnianie kafelków w obrębie kształtu obrazem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f825371d3849e96ace627e660fd7c59bd290185
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a>Porady: wypełnianie kafelków w obrębie kształtu obrazem
Tak samo, jak kafelki mogą być umieszczone obok siebie, aby pokrywał piętra, prostokątne obrazów mogą być umieszczone obok siebie do wypełnienia kształtu (kafelka). Na kafelku wewnątrz kształtu, użyj pędzla tekstury. Podczas konstruowania <xref:System.Drawing.TextureBrush> obiektu, jeden z argumentów przekazać do konstruktora jest <xref:System.Drawing.Image> obiektu. Pędzel tekstury umożliwia malowanie wnętrza kształtu, kształt jest wypełniony powtarzane kopii tego obrazu.  
  
 Właściwość tryb zawijania <xref:System.Drawing.TextureBrush> obiektu określa, jak obraz jest ustawiony jako jest powtarzany w siatce prostokątny. Możesz wprowadzić Kafelki w siatce, że tę samą orientację, można też obrazów Przerzucanie od położenia siatki co do następnego. Przerzucanie może być poziomo, pionowy lub oba. W poniższych przykładach pokazano kafelków z różnymi typami Przerzucanie.  
  
### <a name="to-tile-an-image"></a>Na kafelku obrazu  
  
-   W tym przykładzie używane na poniższej ilustracji 75 x 75 na kafelku prostokąt 200 x 200.  
  
 ![Kafelek 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt z obrazem. Należy zauważyć, że wszystkie Kafelki tę samą orientację; nie ma żadnych Przerzucanie.  
  
 ![Kafelek 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>Aby odwrócić obraz poziomo podczas kafelków  
  
-   W tym przykładzie ten sam obraz x 75 75 są używane do wypełnienia prostokąt 200 x 200. Tryb zawijania jest ustawiony na poziomie Przerzucanie obrazu. Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt z obrazem. Należy pamiętać, że podczas przenoszenia z jednego fragmentu do następnego wiersza danego obrazu jest odwrócony poziomo.  
  
 ![Kafelek 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>Aby odwrócić obraz w pionie podczas kafelków  
  
-   W tym przykładzie ten sam obraz x 75 75 są używane do wypełnienia prostokąt 200 x 200. Tryb zawijania jest ustawiony na Przerzuć obraz w pionie.  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>Aby odwrócić obraz w poziomie i w pionie podczas kafelków  
  
-   W tym przykładzie używa tego samego obrazu x 75 75 na kafelku prostokąt 200 x 200. Tryb zawijania jest ustawiony na Przerzucanie obrazu w poziomie i w pionie. Na poniższej ilustracji przedstawiono sposób wypełniania prostokąt przez obraz. Należy pamiętać, że jak przejść z jednego fragmentu do drugiego w danym wierszu, obraz jest odwrócony poziomo i jak przenieść z jednego fragmentu do następnego w danej kolumnie, obraz jest odwrócony pionowo.  
  
 ![Kafelek 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
