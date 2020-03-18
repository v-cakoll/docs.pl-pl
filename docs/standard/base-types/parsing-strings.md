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
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084312"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w .NET
Operacja analizy konwertuje ciąg reprezentujący typ podstawowy .NET na ten typ podstawowy. Na przykład operacja analizy służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny. Metoda najczęściej używana do wykonywania operacji analizy `Parse` jest metodą. Ponieważ analizowanie jest odwrotną operacją formatowania (która polega na konwertowaniu typu podstawowego na reprezentację ciągu), stosuje się wiele tych samych reguł i konwencji. Podobnie jak formatowanie używa obiektu, <xref:System.IFormatProvider> który implementuje interfejs, aby zapewnić informacje o formatowaniu poufnych <xref:System.IFormatProvider> dla kultury, analizowanie używa również obiektu, który implementuje interfejs, aby określić sposób interpretowania reprezentacji ciągów. Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów numerycznych](../../../docs/standard/base-types/parsing-numeric.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.  
  
 [Analiza składniowa ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy **.NET DateTime.**  
  
 [Analizowanie innych typów ciągów](../../../docs/standard/base-types/parsing-other.md)  
 Opisuje sposób konwertowania ciągów na typy **Char,** **Boolean**i **Enum.**  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 W tym artykule opisano podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatów i dostawcy formatów.  
  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)  
 Opisuje sposób konwertowania typów.  
  
 [Typy podstawowe](../../../docs/standard/base-types/index.md)  
 W tym artykule opisano typowe operacje, które można wykonać na typach podstawowych .NET.
