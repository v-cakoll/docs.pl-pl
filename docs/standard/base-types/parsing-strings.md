---
title: Analizowanie ciągów w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567747"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w .NET
Operacja związana konwertuje ciąg reprezentujący typ podstawowy .NET do tego typu podstawowego. Na przykład operacji analizy służy do przekonwertowania ciągu liczba zmiennoprzecinkowa lub wartości daty i godziny. Metoda najczęściej używane do wykonywania operacji przetwarzania jest `Parse` metody. Ponieważ analiza jest odwrotnej operacji formatowania (co wymaga konwersji typu podstawowego do reprezentacji ciągu), wiele tych samych reguł i konwencje zastosowania. Tylko jako formatowania używa obiektu implementującego <xref:System.IFormatProvider> informacje zależne od kultury formatowania, analizowania również używa obiektu implementującego interfejs <xref:System.IFormatProvider> interfejsu, aby określić sposób interpretowania reprezentacji w postaci ciągu . Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)  
 Opisuje sposób konwertowania ciągów na typy liczbowe .NET.  
  
 [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)  
 Opisuje sposób konwertowania ciągów na .NET **DateTime** typów.  
  
 [Analizowanie innych typów ciągów](../../../docs/standard/base-types/parsing-other.md)  
 Opisuje sposób konwertowania ciągów do **Char**, **logiczna**, i **wyliczenia** typów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 W tym artykule opisano podstawowe pojęcia dotyczące formatowania, takich jak specyfikatory formatu i dostawców formatu.  
  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)  
 Opisuje sposób konwertowania typów.  
  
 [Typy podstawowe](../../../docs/standard/base-types/index.md)  
 W tym artykule opisano typowe operacje, które można wykonywać na typy podstawowe .NET.
