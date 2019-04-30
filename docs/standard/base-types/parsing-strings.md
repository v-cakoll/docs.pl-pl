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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766002"
---
# <a name="parsing-strings-in-net"></a>Analizowanie ciągów w programie .NET
Operacji analizowania konwertuje ciąg reprezentujący typ podstawowy .NET do tego typu podstawowego. Na przykład operacji analizowania służy do przekonwertowania ciągu na liczbę zmiennoprzecinkową lub wartości daty i godziny. Metoda najczęściej używany do wykonywania operacji analizowania `Parse` metody. Ponieważ analiza jest odwrotna operacją formatowania (co wymaga konwersji typu podstawowego na jego reprezentację ciągu), wiele tych samych reguł i Konwencji zastosowanie. Podobnie jak formatowanie używa obiekt, który implementuje <xref:System.IFormatProvider> interfejsu, aby zapewnić kultury informacje o formatowaniu, analizowania również używa obiekt, który implementuje <xref:System.IFormatProvider> interfejsu, aby określić sposób interpretowania reprezentację ciągu znaków . Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Analizowanie ciągów liczbowych](../../../docs/standard/base-types/parsing-numeric.md)  
 W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.  
  
 [Analizowanie ciągów daty i godziny](../../../docs/standard/base-types/parsing-datetime.md)  
 W tym artykule opisano sposób konwertowania ciągów w środowisku .NET **daty/godziny** typów.  
  
 [Analizowanie innych typów ciągów](../../../docs/standard/base-types/parsing-other.md)  
 W tym artykule opisano sposób konwertowania ciągów do **Char**, **logiczna**, i **wyliczenia** typów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)  
 W tym artykule opisano podstawowe pojęcia formatowania, takich jak specyfikatorów formatu i format dostawców.  
  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)  
 W tym artykule opisano sposób konwertowania typów.  
  
 [Typy podstawowe](../../../docs/standard/base-types/index.md)  
 W tym artykule opisano typowe operacje, które można wykonywać na typy podstawowe dla platformy .NET.
