---
title: 'Instrukcje: Obracanie, odzwierciedlanie i pochylanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 505028c491228ffdf9c11d0c71dcd5e1afdc5103
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59114052"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Instrukcje: Obracanie, odzwierciedlanie i pochylanie obrazów
Można obracanie, odzwierciedlanie i pochylanie obrazów, określając docelowe punkty narożników lewym, prawym górnym rogu i lewym dolnym oryginalnego obrazu. Docelowe trzy punkty określają affine — przekształcenia, które mapuje równoległobok oryginalny obraz prostokątny.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że oryginalny obraz jest prostokąt z lewego górnego rogu w (0, 0), w prawym górnym rogu w (100, 0) i lewego dolnego rogu w (0, 50). Teraz załóżmy, że możesz mapować te trzy wskazuje docelowe punkty w następujący sposób.  
  
|Oryginalny punkt|Docelowy punkt|  
|--------------------|-----------------------|  
|Lewa górna (0, 0)|(200, 20)|  
|W prawym górnym (100, 0)|(110, 100)|  
|Lewej dolnej (0, 50)|(250, 30)|  
  
 Na poniższej ilustracji pokazuje oryginalny obraz i obraz, który mapowany do równoległobok. Oryginalny obraz ma zostały nierówne, zostaną uwzględnione, obracać i translacji. Oś x wzdłuż górnej krawędzi oryginalny obraz jest mapowany na wierszu, który jest uruchamiany za pośrednictwem (200, 20) i (110, 100). Oś y wzdłuż lewej krawędzi oryginalny obraz jest mapowany na wierszu, który jest uruchamiany za pośrednictwem (200, 20) i (250, 30).  
  
 ![Oryginalny obraz i obraz, który mapowany do równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-illustration.gif)  
  
 Na poniższej ilustracji przedstawiono podobne przekształcenie zastosowane do obrazu fotograficzne:  
  
 ![Obraz obiekt climber i obraz mapowane na równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-photo.png)  
  
 Na poniższej ilustracji przedstawiono podobne przekształcenie zastosowane do metaplik:  
  
 ![Ilustracja kształtów, tekstu i że mapowane na równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-metafile.png)  
  
 Poniższy przykład tworzy obrazy z pierwszą ilustracją.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Upewnij się zastąpić `Stripes.bmp` ze ścieżką do obrazu, który jest prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
