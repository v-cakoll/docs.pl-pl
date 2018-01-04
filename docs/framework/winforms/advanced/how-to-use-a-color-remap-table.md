---
title: "Porady: używanie tabeli ponownego mapowania kolorów"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e208aa9c98c1ca19baee83760cfd0f75972ecfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-remap-table"></a>Porady: używanie tabeli ponownego mapowania kolorów
Ponowne mapowanie jest proces konwersji kolorów obrazu zgodnie z tabeli ponownego mapowania kolorów. Tabeli ponownego mapowania kolorów jest tablicą <xref:System.Drawing.Imaging.ColorMap> obiektów. Każdy <xref:System.Drawing.Imaging.ColorMap> obiektu w tablicy ma <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> właściwości i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwości.  
  
 Gdy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rysuje jako obraz każdego piksela obrazu jest porównywany z tablicy kolorów stary. Jeśli koloru piksela pasuje do starego kolorów, kolor jest zmieniany na odpowiednich nowy kolor. Kolory są zmieniane tylko w przypadku renderowania — wartości kolorów samego obrazu (przechowywane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiektu) nie są zmieniane.  
  
 Aby narysować ponownie zmapowany obrazu, zainicjowania tablicy <xref:System.Drawing.Imaging.ColorMap> obiektów. Przekaż tej tablicy do <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metody <xref:System.Drawing.Imaging.ImageAttributes> obiekt, a następnie przekazać <xref:System.Drawing.Imaging.ImageAttributes> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku RemapInput.bmp. Kod tworzy składający się z pojedynczej tabeli ponownego mapowania kolorów <xref:System.Drawing.Imaging.ColorMap> obiektu. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Właściwość `ColorRemap` obiekt jest czerwony i <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> właściwość jest niebieski. Obraz jest rysowane raz bez ponownego mapowania, a drugi raz z ponownego mapowania. Proces ponownego mapowania zmienia wszystkich red pikseli na niebieski.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i ponownie zmapowany obraz po prawej stronie.  
  
 ![Ponowne mapowanie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
