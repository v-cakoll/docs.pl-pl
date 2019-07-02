---
title: Używanie kodeków obrazu w zarządzanym GDI+
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: 8cd66f3ce3da462867da9e23c38b3f6d877c058c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505088"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a>Używanie kodeków obrazu w zarządzanym GDI+
<xref:System.Drawing> Przestrzeń nazw zawiera <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowania obrazami. Za pomocą kodery obrazów w GDI +, można napisać obrazów z pamięci na dysk. Za pomocą dekodery obrazów w GDI +, należy załadować obrazy z dysku do pamięci. Koder przekształca dane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiekt do formatu pliku wyznaczonym dysku. Dekoder przekształca dane w pliku dysku do formatu wymaganego przez <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów.  
  
 GDI + ma wbudowane kodeków, które obsługują następujące typy plików:  
  
- BMP  
  
- GIF  
  
- JPEG  
  
- PNG  
  
- TIFF  
  
 GDI + ma również wbudowane dekoderów, które obsługują następujące typy plików:  
  
- WMF  
  
- EMF  
  
- ICON  
  
 W poniższych tematach omówiono kodeków bardziej szczegółowo:  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Lista zainstalowanych koderów](how-to-list-installed-encoders.md)  
 Opisuje sposób wyświetlenia listy przypadku koderów dostępnych na komputerze.  
  
 [Instrukcje: Lista zainstalowanych dekoderów](how-to-list-installed-decoders.md)  
 Opisuje sposób wyświetlenia listy dekodery dostępne na komputerze.  
  
 [Instrukcje: Określanie parametrów obsługiwanych przez koder](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 W tym artykule opisano sposób wyświetlenia listy <xref:System.Drawing.Imaging.EncoderParameters> obsługiwanych przez koder.  
  
 [Instrukcje: Konwertowanie obrazu BMP na format PNG](how-to-convert-a-bmp-image-to-a-png-image.md)  
 W tym artykule opisano, jak zapisać obraz w formacie inny obraz.  
  
 [Instrukcje: Ustawianie poziomu dekompresji JPEG](how-to-set-jpeg-compression-level.md)  
 W tym artykule opisano, jak zmienić poziom jakości obrazu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Informacje o kodzie zarządzanym GDI+](about-gdi-managed-code.md)  
  
 [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
