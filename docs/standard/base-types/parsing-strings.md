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
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523805"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w .NET
Operacja analizowania konwertuje ciąg reprezentujący typ podstawowy platformy .NET na ten typ podstawowy. Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny. Metoda najczęściej używana do wykonywania operacji analizy jest `Parse` metoda. Ponieważ analizowanie jest odwrotną operacją formatowania (która polega na konwersji typu podstawowego na jego reprezentację ciągu), stosuje się wiele tych samych reguł i konwencji. Podobnie jak formatowanie używa obiektu, <xref:System.IFormatProvider> który implementuje interfejs, aby zapewnić informacje o formatowaniu zależne <xref:System.IFormatProvider> od kultury, analizowanie używa również obiektu, który implementuje interfejs, aby określić sposób interpretowania reprezentacji ciągów. Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.  
  
 [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy **.NET DateTime.**  
  
 [Analiza składniowa innych ciągów](../../../docs/standard/base-types/parsing-other.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy **Char,** **Boolean**i **Enum.**  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 Zawiera opis podstawowych pojęć formatowania, takich jak specyfikatory formatów i dostawcy formatów.  
  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)  
 W tym artykule opisano sposób konwertowania typów.
