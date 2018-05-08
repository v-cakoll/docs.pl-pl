---
title: 'Porady: konwertowanie obrazu w formacie BMP na format PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: fd890c4f17b9759d37d7625526366034c664a71a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a>Porady: konwertowanie obrazu w formacie BMP na format PNG
Często należy przekonwertować z jednego obrazu pliku formatu do innego. Wykonaj tę konwersję łatwo wywołując <xref:System.Drawing.Image.Save%2A> metody <xref:System.Drawing.Image> klasy i określając <xref:System.Drawing.Imaging.ImageFormat> formatu pliku odpowiedni obraz.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ładuje obrazu w formacie BMP z typem, a następnie zapisuje obraz w formacie PNG.  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Aplikacji formularzy systemu Windows.  
  
-   Odwołanie do `System.Drawing.Imaging` przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: lista zainstalowanych koderów](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [Używanie kodeków obrazu w zarządzanym GDI+](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [Typy map bitowych](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
