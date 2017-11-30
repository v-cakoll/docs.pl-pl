---
title: Kodowanie pliku (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: deaab4371ab0d5d15c627bfd6352a7090bf08024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
