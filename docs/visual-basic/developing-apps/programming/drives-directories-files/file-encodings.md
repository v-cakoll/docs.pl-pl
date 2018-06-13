---
title: Kodowanie pliku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 30aba517b3b0fbb5fa5bea48134934b2c2d26e50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582289"
---
# <a name="file-encodings-visual-basic"></a>Kodowanie pliku (Visual Basic)
Kodowanie pliku, znanej także jako kodowanie znaków, określ sposób wyświetlania znaków podczas przetwarzania tekstu. Kodowań może być preferowana zamiast innego pod względem znaków języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany.  
  
 Gdy odczyt lub zapis do plików, nieprawidłowo dopasowania kodowanie pliku może spowodować wyjątków lub niepoprawne wyniki.  
  
## <a name="types-of-encodings"></a>Typy kodowania  
 Unicode jest preferowaną metodę kodowania, podczas pracy z plikami. Unicode jest na całym świecie standard kodowania znaków, który używa wartości 16-bitowego kodu do reprezentowania wszystkich znaków używany w obliczeniu nowoczesnych tym techniczne symboli i znaków specjalnych w publikowania.  
  
 Wcześniejsze standardy kodowania znaków obejmowały zestawów tradycyjnych znaków, takich jak zestaw znaków ANSI systemu Windows, który używa wartości 8-bitowego kodu lub kombinacji wartości 8-bitowych, do reprezentowania znaki używane w określonym języku lub regionu geograficznego.  
  
## <a name="encoding-class"></a>Kodowanie — klasa  
 <xref:System.Text.Encoding> Klasa reprezentuje kodowania znaków. Ta tabela zawiera typ kodowania dostępny i zawiera opis każdego.  
  
|Nazwa|Opis|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|Reprezentuje kodowania znaków ASCII znaków Unicode.|  
|<xref:System.Text.UnicodeEncoding>|Reprezentuje kodowania UTF-16 znaków Unicode.|  
|<xref:System.Text.UTF32Encoding>|Reprezentuje kodowania UTF-32 znaków Unicode.|  
|<xref:System.Text.UTF7Encoding>|Reprezentuje kodowania UTF-7 znaków Unicode.|  
|<xref:System.Text.UTF8Encoding>|Reprezentuje kodowania UTF-8 znaków Unicode.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
