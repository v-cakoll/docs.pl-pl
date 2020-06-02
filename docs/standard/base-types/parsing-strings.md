---
title: Analizowanie ciągów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277417"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w programie .NET
Operacja analizowania konwertuje ciąg, który reprezentuje typ podstawowy platformy .NET do tego typu podstawowego. Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny. Metoda najczęściej używana do wykonywania operacji analizowania jest `Parse` metodą. Ponieważ analizowanie jest operacją wsteczną formatowania (która wymaga przekonwertowania typu bazowego na jego reprezentację ciągu), mają zastosowanie wiele z tych samych zasad i Konwencji. Tak samo jak formatowanie korzysta z obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby zapewnić informacje o formatowaniu z uwzględnieniem kultury, podczas analizy używa również obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby określić sposób interpretowania przedstawienia ciągu. Aby uzyskać więcej informacji, zobacz [Typy formatowania](formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów liczbowych](parsing-numeric.md)  
 Opisuje sposób konwersji ciągów na typy liczbowe platformy .NET.  
  
 [Analizowanie ciągów daty i godziny](parsing-datetime.md)  
 Opisuje sposób konwertowania ciągów na typy **datetimes** platformy .NET.  
  
 [Analiza składniowa innych ciągów](parsing-other.md)  
 Opisuje sposób konwersji ciągów na typy **znaków**, **wartości logicznych**i typów **wyliczeniowych** .  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](formatting-types.md)  
 Opisuje podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatu i dostawcy formatowania.  
  
 [Konwersja typów w programie .NET](type-conversion.md)  
 Opisuje sposób konwersji typów.
