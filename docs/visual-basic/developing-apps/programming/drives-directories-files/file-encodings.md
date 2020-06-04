---
title: Kodowanie pliku
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: f906b2f2d747a7950c70a24549bbf5423e5b87b4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401748"
---
# <a name="file-encodings-visual-basic"></a>Kodowanie pliku (Visual Basic)

Kodowanie plików, znane także jako kodowania znaków, określają sposób reprezentowania znaków podczas przetwarzania tekstu. Jedno kodowanie może być preferowane przez inne warunki języka, które może lub nie może obsłużyć, chociaż standard Unicode jest zazwyczaj preferowany.

Podczas odczytywania z plików lub zapisywania do nich niewłaściwie dopasowane kodowania plików mogą spowodować wyjątki lub nieprawidłowe wyniki.

## <a name="types-of-encodings"></a>Typy kodowań

Unicode jest preferowanym kodowaniem podczas pracy z plikami. Unicode to ogólnoświatowy standard kodowania znaków, który używa wartości 16-bitowych kodu do reprezentowania wszystkich znaków używanych w nowoczesnych obliczeniach, w tym symboli technicznych i znaków specjalnych używanych do publikowania.

Poprzednie standardy kodowania znaków składają się z tradycyjnych zestawów znaków, takich jak zestaw znaków ANSI systemu Windows, który używa wartości 8-bitowych lub kombinacji wartości 8-bitowych, aby reprezentować znaki używane w konkretnym języku lub regionie geograficznym.

## <a name="encoding-class"></a>Klasa kodowania

<xref:System.Text.Encoding>Klasa reprezentuje kodowanie znaków. W tej tabeli przedstawiono typ dostępnych kodowań i opisano poszczególne z nich.

|Nazwa|Opis|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Reprezentuje kodowanie znaków ASCII znaków Unicode.|
|<xref:System.Text.UnicodeEncoding>|Reprezentuje kodowanie UTF-16 znaków Unicode.|
|<xref:System.Text.UTF32Encoding>|Reprezentuje kodowanie UTF-32 znaków Unicode.|
|<xref:System.Text.UTF7Encoding>|Reprezentuje kodowanie UTF-7 znaków Unicode.|
|<xref:System.Text.UTF8Encoding>|Reprezentuje kodowanie UTF-8 znaków Unicode.|

## <a name="see-also"></a>Zobacz też

- [Odczyt z plików](reading-from-files.md)
- [Zapisywanie w plikach](writing-to-files.md)
