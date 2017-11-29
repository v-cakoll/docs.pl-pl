---
title: "Porady: używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10a0ef4e7fd8514245a7659dd515d8f363a716ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Porady: używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania
Tryb interpolacji <xref:System.Drawing.Graphics> obiektu wpływa na sposób [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obrazów w skali (odcinkach i zmniejsza). <xref:System.Drawing.Drawing2D.InterpolationMode> Wyliczenie definiuje kilka trybów interpolacji, niektóre z nich są wyświetlane na poniższej liście:  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Do rozciągania obrazów, każdego piksela oryginalnego obrazu muszą być zamapowane do grupy pikseli większy obraz. Aby zmniejszyć rozmiar obrazu, grup pikseli oryginalnego obrazu musi być zamapowany na jednym pikseli mniejsze. Skuteczność algorytmy, które wykonują te mapowania określa jakość skalowanie obrazu. Algorytmy, które powodują powstanie wyższej jakości skalowane obrazy zwykle wymagają więcej czasu przetwarzania. Na powyższej liście <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> jest tryb najniższym jakości i <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> jest tryb najwyższej jakości.  
  
 Aby ustawić tryb interpolacji, przypisać jeden z elementów członkowskich <xref:System.Drawing.Drawing2D.InterpolationMode> wyliczeniu, aby <xref:System.Drawing.Graphics.InterpolationMode%2A> właściwość <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="example"></a>Przykład  
 Rysuje obraz, zmniejsza rozmiar obrazu z trzech trybów różnych interpolacji w następującym przykładzie.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu i trzy obrazy mniejsze.  
  
 ![Obraz ze zróżnicowanymi ustawieniami interpolacji](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikony i metapliki](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
