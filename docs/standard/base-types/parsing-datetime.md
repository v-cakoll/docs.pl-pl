---
title: "Analizowanie ciągów daty i godziny w programie .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analizowanie ciągów daty i godziny w .NET
Metody analizy Konwertuj reprezentację ciągu daty i godziny na równoważne <xref:System.DateTime> obiektu. <xref:System.DateTime.Parse%2A> i <xref:System.DateTime.TryParse%2A> metody konwersja kilka typowych liczbami w postaci daty i godziny. <xref:System.DateTime.ParseExact%2A> i <xref:System.DateTime.TryParseExact%2A> metody konwersji reprezentację ciągu, który jest zgodny z wzorcem określona przez ciąg formatu daty i godziny. (Zobacz tematy na [standardowa Data i godzina ciągi formatujące](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 Podczas analizowania ma wpływ właściwości dostawcy formatu, który dostarcza informacje, takie jak ciągi daty i czasu separatorów i nazwy miesięcy, dni i Arial. Dostawca formatu jest bieżącą <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest dostarczany niejawnie według bieżącej kultury wątku lub jawnie <xref:System.IFormatProvider> parametr metody analizy. Dla <xref:System.IFormatProvider> parametru, określ <xref:System.Globalization.CultureInfo> obiektu, który reprezentuje kultury, lub <xref:System.Globalization.DateTimeFormatInfo> obiektu.  
  
 Reprezentacja ciągu daty do przeanalizowania musi zawierać miesiąca i co najmniej jeden dzień lub rok. Reprezentacja ciągu czasu musi zawierać godzinę i co najmniej minut lub wskaźnik AM/PM. Jednak jeśli to możliwe analizowania dostaw wartości domyślne dla składników został pominięty. Brak daty domyślne ustawienia do bieżącej daty, brak roku, wartością domyślną będzie bieżącego roku, brak dzień miesiąca wartości domyślne do pierwszego dnia miesiąca, oraz czasu brak domyślnie przyjmowana północ.  
  
 Jeśli reprezentacja ciągu określa tylko raz, podczas analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, i <xref:System.DateTime.Day%2A> właściwości mają odpowiednie wartości <xref:System.DateTime.Today%2A> właściwości. Jednak jeśli <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> stała jest określona w metodę analizowania, wynikowy rok, miesiąc i dzień właściwości są ustawione na wartość `1`.  
  
 Oprócz daty i czasu składnika reprezentację ciągu daty i godziny mogą obejmować przesunięcie, która wskazuje, ile czasu różni się od uniwersalny czas koordynowany (UTC). Na przykład ciąg "2007-2-14 5:32:00 -7:00" definiuje czas, który jest siedem godziny wcześniejszy niż czas UTC. W przypadku pominięcia przesunięcie z reprezentacji ciągu czas analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> ustawioną właściwość <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Jeśli określono przesunięcia, analizowania zwraca <xref:System.DateTime> obiekt z jego <xref:System.DateTime.Kind%2A> ustawioną właściwość <xref:System.DateTimeKind.Local> i jego wartość dostosowana do lokalnej strefy czasowej komputera. To zachowanie można zmienić za pomocą <xref:System.Globalization.DateTimeStyles> stałej metodą analizy.  
  
 Dostawca formatu służy również do interpretowania niejednoznaczne daty liczbowych. Na przykład go nie jest jasne są składniki daty reprezentowany przez ciąg "02/03/04" dzień, miesiąc i rok. W takim przypadku składniki są interpretowane zgodnie z kolejnością podobne formaty daty w formacie dostawcy.  
  
## <a name="parse"></a>analizy  
 W poniższym przykładzie przedstawiono użycie **przeanalizować** metody do przekonwertowania ciągu na **DateTime**. W tym przykładzie użyto kultury skojarzone z bieżącym wątku do wykonania analizy. Jeśli <xref:System.Globalization.CultureInfo> skojarzone z bieżącej kultury nie może przeanalizować składni ciągu wejściowego <xref:System.FormatException> jest generowany.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Można również określić **CultureInfo** ustawione na jedną kultur wynika z tego obiektu lub można określić jeden ze standardowych <xref:System.Globalization.DateTimeFormatInfo> obiekty zwrócone przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Poniższy przykład kodu wykorzystuje dostawca formatu do analizowania niemieckim do **DateTime**. A **CultureInfo** reprezentujący kultury de-DE jest zdefiniowana i przekazany z ciągiem przetwarzane w celu zapewnienia pomyślnego analizowania tego określonego ciągu. Wykluczy to niezależnie od ustawienie znajduje się w **CurrentCulture** z **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 Jednak mimo że używasz przeciążeń <xref:System.DateTime.Parse%2A> metodę, aby określić dostawców formatu niestandardowego, metoda nie obsługuje korzystania z niestandardowym formacie dostawców. Aby przeanalizować daty i czasu wyrażona w niestandardowym formacie, użyj <xref:System.DateTime.ParseExact%2A> metody zamiast tego.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Globalization.DateTimeStyles> wyliczeniu, aby określić, że nie można dodać bieżących informacji o datę i godzinę do **DateTime** dla pól, które nie definiuje ciąg.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> Metoda konwertuje ciąg zgodny wzorzec określony ciąg **DateTime** obiektu. Ciąg, który nie jest w formie określony jest przekazany do tej metody <xref:System.FormatException> jest generowany. Można określić jedną z standardowa Data i godzina specyfikatory formatu lub ograniczona kombinację niestandardowa data i godzina specyfikatory formatu. Używanie specyfikatorów formatu niestandardowego, jest można skonstruować ciąg rozpoznawania niestandardowych. Aby uzyskać informacje o Specyfikatory, zobacz Tematy w [standardowa Data i godzina ciągi formatujące](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) i [niestandardowa data i godzina ciągi formatujące](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Każdy przeciążenia <xref:System.DateTime.ParseExact%2A> ma również metody <xref:System.IFormatProvider> parametr, który zwykle zawiera informacje specyficzne dla kultury dotyczące formatowania ciągu. Zwykle to <xref:System.IFormatProvider> obiekt jest <xref:System.Globalization.CultureInfo> obiekt, który reprezentuje standardowe kultury lub <xref:System.Globalization.DateTimeFormatInfo> obiektu, który jest zwracany przez <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> właściwości. Jednak w przeciwieństwie do innych Data i godzina funkcje analizy, ta metoda obsługuje również <xref:System.IFormatProvider> definiuje niestandardowy format daty i godziny.  
  
 W poniższym przykładzie kodu **ParseExact** metody jest przekazywany obiekt ciągu do analizy, następuje specyfikatora formatu, a następnie **CultureInfo** obiektu. To **ParseExact** metody można analizować tylko ciągi, które wykazują wzorzec daty długiej w kultury en US.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie ciągów](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatowanie tekstu](../../../docs/standard/base-types/formatting-types.md)  
 [Konwersja typów w .NET](../../../docs/standard/base-types/type-conversion.md)
