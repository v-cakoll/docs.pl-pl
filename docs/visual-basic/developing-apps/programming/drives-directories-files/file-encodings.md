---
title: Kodowanie pliku
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348890"
---
# <a name="file-encodings-visual-basic"></a>Kodowanie pliku (Visual Basic)

Kodowanie plików, znane również jako kodowanie znaków, określa sposób reprezentowania znaków podczas przetwarzania tekstu. Jedno kodowanie może być korzystne w stosunku do innego pod względem znaków języka, które może lub nie może obsłużyć, chociaż Unicode jest zwykle preferowane.

Podczas odczytywania lub zapisywania do plików nieprawidłowo pasujące kodowania plików może spowodować wyjątki lub nieprawidłowe wyniki.

## <a name="types-of-encodings"></a>Typy kodowania

Unicode jest preferowanym kodowaniem podczas pracy z plikami. Unicode to światowy standard kodowania znaków, który używa 16-bitowych wartości kodu do reprezentowania wszystkich znaków używanych w nowoczesnych komputerach, w tym symboli technicznych i znaków specjalnych używanych w publikowaniu.

Poprzednie standardy kodowania znaków składały się z tradycyjnych zestawów znaków, takich jak zestaw znaków ANSI systemu Windows, który używa 8-bitowych wartości kodu lub kombinacji wartości 8-bitowych do reprezentowania znaków używanych w określonym języku lub regionie geograficznym.

## <a name="encoding-class"></a>Klasa kodowania

Klasa <xref:System.Text.Encoding> reprezentuje kodowanie znaków. W tej tabeli wymieniono typ dostępnych kodowania i opisano każdy z nich.

|Nazwa|Opis|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Reprezentuje kodowanie znaków ASCII znaków Unicode.|
|<xref:System.Text.UnicodeEncoding>|Reprezentuje kodowanie UTF-16 znaków Unicode.|
|<xref:System.Text.UTF32Encoding>|Reprezentuje kodowanie UTF-32 znaków Unicode.|
|<xref:System.Text.UTF7Encoding>|Reprezentuje kodowanie ZNAKÓW Unicode w u. UTF-7.|
|<xref:System.Text.UTF8Encoding>|Reprezentuje kodowanie ZNAKÓW Unicode w u. UTF-8.|

## <a name="see-also"></a>Zobacz też

- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
