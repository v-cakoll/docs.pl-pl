---
title: "Używanie kodeków obrazu w zarządzanym GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Używanie kodeków obrazu w zarządzanym GDI+
<xref:System.Drawing> Przestrzeń nazw zawiera <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowanie obrazów. Za pomocą kodery obrazów w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można zapisać obrazy z pamięci na dysku. Za pomocą dekodery obrazów w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można załadować obrazów z dysku do pamięci. Koder tłumaczy dane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiekt do formatu pliku wyznaczonych dysku. Dekoder tłumaczy dane w pliku dysku format wymagany przez <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]zawiera wbudowane kodeków obsługujących następujące typy plików:  
  
-   BMP  
  
-   GIF  
  
-   JPEG  
  
-   PNG  
  
-   TIFF  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]ma również wbudowane dekoderów, które obsługują następujące typy plików:  
  
-   WMF  
  
-   EMF  
  
-   IKONA  
  
 W poniższych tematach opisano kodeków bardziej szczegółowo:  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: lista zainstalowanych koderów](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 Opisuje sposób listy koderów dostępne na komputerze.  
  
 [Porady: lista zainstalowanych dekoderów](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 Opisuje sposób wyświetlania dekodery dostępne na komputerze.  
  
 [Porady: Określanie parametrów obsługiwanych przez koder](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 Opisuje sposób wyświetlania <xref:System.Drawing.Imaging.EncoderParameters> obsługiwanych przez koder.  
  
 [Porady: Konwertowanie obrazu w formacie BMP na obrazu PNG](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 Opisuje sposób zapisywania obraz w formacie inny obraz.  
  
 [Porady: Ustawianie poziomu dekompresji JPEG](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 Zawiera opis sposobu zmiany poziomu jakości obrazu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kodzie zarządzanym GDI + — informacje](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
