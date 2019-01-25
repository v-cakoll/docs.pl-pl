---
title: 'Instrukcje: Konwertowanie obrazu BMP na format PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: e11e2874853fb924b2da09f9fdc986873941f141
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676448"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Instrukcje: Konwertowanie obrazu BMP na format PNG
Często należy przekonwertować z jednego obrazu pliku formatu do innego. Możesz łatwo zrobić ta konwersja przez wywołanie metody <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy i określając <xref:System.Drawing.Imaging.ImageFormat> dla formatu plików odpowiedni obraz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład załaduje obraz BMP z typem, a następnie zapisuje obraz w formacie PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacja Windows Forms.  
  
-   Odwołanie do `System.Drawing.Imaging` przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Lista zainstalowanych koderów](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
- [Typy map bitowych](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
