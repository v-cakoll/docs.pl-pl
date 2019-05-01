---
title: Kodowanie pliku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960189"
---
# <a name="file-encodings-visual-basic"></a>Kodowanie pliku (Visual Basic)
Określ kodowanie pliku, znany także jako kodowanie znaków do reprezentowania znaków, kiedy przetwarzanie tekstu. Jednego formatu kodowania może być preferowane zamiast innego pod względem znaki języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany.  
  
 Gdy odczytujemy ze zmiennej czy zapisywanie w plikach, nieprawidłowo dopasowania kodowanie pliku może spowodować wyjątków lub niepoprawne wyniki.  
  
## <a name="types-of-encodings"></a>Typy kodowania  
 Unicode jest preferowaną metodę kodowania, podczas pracy z plikami. Unicode jest na całym świecie standard kodowania znaków, który używa wartości 16-bitowego kodu, który reprezentuje wszystkie znaki, które są stosowane w nowoczesnych obliczeń, w tym techniczne symboli i znaków specjalnych, używane podczas publikowania w.  
  
 Wcześniejsze standardy kodowania znaków składa się z zestawów znaków tradycyjnych, takich jak zestawu znaków Windows ANSI, który używa wartości 8-bitowego kodu lub kombinacji wartości 8-bitowych, który reprezentuje znaki używane w określonym języku lub regionu geograficznego.  
  
## <a name="encoding-class"></a>Klasa kodowania  
 <xref:System.Text.Encoding> Klasa reprezentuje kodowania znaków. Ta tabela zawiera typ kodowania dostępne i zawiera opis każdego.  
  
|Nazwa|Opis|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|Reprezentuje kodowania znaków ASCII znaków Unicode.|  
|<xref:System.Text.UnicodeEncoding>|Reprezentuje kodowanie UTF-16 znaków Unicode.|  
|<xref:System.Text.UTF32Encoding>|Reprezentuje kodowania UTF-32 znaków Unicode.|  
|<xref:System.Text.UTF7Encoding>|Reprezentuje kodowania UTF-7 znaków Unicode.|  
|<xref:System.Text.UTF8Encoding>|Reprezentuje kodowania UTF-8 znaków Unicode.|  
  
## <a name="see-also"></a>Zobacz także

- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
