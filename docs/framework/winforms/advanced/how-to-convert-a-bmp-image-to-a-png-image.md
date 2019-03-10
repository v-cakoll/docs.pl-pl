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
ms.openlocfilehash: f8636bea120aee86c795b4196415145a484e5772
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725002"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Instrukcje: Konwertowanie obrazu BMP na format PNG
Często należy przekonwertować z jednego obrazu pliku formatu do innego. Możesz łatwo zrobić ta konwersja przez wywołanie metody <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy i określając <xref:System.Drawing.Imaging.ImageFormat> dla formatu plików odpowiedni obraz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład załaduje obraz BMP z typem, a następnie zapisuje obraz w formacie PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacja Windows Forms.  
  
-   Odwołanie do `System.Drawing.Imaging` przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Lista zainstalowanych koderów](how-to-list-installed-encoders.md)
- [Używanie kodeków obrazu w zarządzanym GDI+](using-image-encoders-and-decoders-in-managed-gdi.md)
- [Typy map bitowych](types-of-bitmaps.md)
