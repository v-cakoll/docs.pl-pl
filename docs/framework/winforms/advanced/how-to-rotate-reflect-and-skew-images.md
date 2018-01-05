---
title: "Porady: obracanie, odzwierciedlanie i pochylanie obrazów"
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
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 163af74d27adcb7ec720a54bfd969bd704f7b1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Porady: obracanie, odzwierciedlanie i pochylanie obrazów
Można obracanie, odzwierciedlanie i pochylanie obrazów, określając punkty docelowe narożników lewym górnym, prawym górnym i lewym dolnym oryginalnego obrazu. Punkty docelowe trzy określają affine — przekształcenia mapowanego oryginalnego obrazu prostokątne równoległobok.  
  
## <a name="example"></a>Przykład  
 Załóżmy na przykład, oryginalnego obrazu jest prostokąt z lewym górnym rogu na (0, 0), prawym górnym rogu na (100, 0) i lewym dolnym rogu na (0, 50). Teraz załóżmy, że możesz mapować te trzy wskazuje punkty docelowe w następujący sposób.  
  
|Oryginalny punkt|Punkt docelowy|  
|--------------------|-----------------------|  
|Lewej górnej (0, 0)|(200, 20)|  
|Prawy górny (100, 0)|(110, 100)|  
|Lewym dolnym (0, 50)|(250, 30)|  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu i mapowane na równoległobok obrazu. Oryginalny obraz ma został niesymetryczna, zostaną uwzględnione obracać i translacji. Oś x wzdłuż górnej krawędzi oryginalnego obrazu jest zamapowana na wiersz, który jest uruchamiany za pośrednictwem (200, 20) i (110, 100). Oś y wzdłuż lewej krawędzi oryginalnego obrazu jest zamapowana na wiersz, który jest uruchamiany za pośrednictwem (200, 20) i (250, 30).  
  
 ![Rozkłada](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 Na poniższej ilustracji przedstawiono transformację podobne do fotograficzne obrazu.  
  
 ![Przekształcony obiekt Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 Na poniższej ilustracji przedstawiono transformację podobne dotyczą metaplik.  
  
 ![Przekształcone metaplik](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 Poniższy przykład tworzy obrazy ilustracją pierwszy.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Upewnij się zastąpić `Stripes.bmp` ze ścieżką do obrazu, który jest prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
