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
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084312"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w programie .NET
Operacja analizowania konwertuje ciąg, który reprezentuje typ podstawowy platformy .NET do tego typu podstawowego. Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny. Metoda najczęściej używana do wykonywania operacji analizowania jest metodą `Parse`. Ponieważ analizowanie jest operacją wsteczną formatowania (która wymaga przekonwertowania typu bazowego na jego reprezentację ciągu), mają zastosowanie wiele z tych samych zasad i Konwencji. Podobnie jak formatowanie korzysta z obiektu, który implementuje interfejs <xref:System.IFormatProvider>, aby zapewnić informacje o formatowaniu z uwzględnieniem kultury, podczas analizowania używa również obiektu, który implementuje interfejs <xref:System.IFormatProvider>, aby określić sposób interpretowania reprezentacji ciągu. Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)  
 Opisuje sposób konwersji ciągów na typy liczbowe platformy .NET.  
  
 [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)  
 Opisuje sposób konwertowania ciągów na typy **datetimes** platformy .NET.  
  
 [Analizowanie innych typów ciągów](../../../docs/standard/base-types/parsing-other.md)  
 Opisuje sposób konwersji ciągów na typy **znaków**, **wartości logicznych**i typów **wyliczeniowych** .  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 Opisuje podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatu i dostawcy formatowania.  
  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)  
 Opisuje sposób konwersji typów.  
  
 [Typy podstawowe](../../../docs/standard/base-types/index.md)  
 Opisuje Typowe operacje, które można wykonywać na podstawowych typach .NET.
