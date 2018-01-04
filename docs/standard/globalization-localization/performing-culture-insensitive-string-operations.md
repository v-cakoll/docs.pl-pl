---
title: "Wykonywanie niezależnych od kultury operacji na ciągach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62aa839d2dae2f6dc84d529a8abf5061367f221f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations"></a>Wykonywanie niezależnych od kultury operacji na ciągach
Większości metod .NET Framework, które wykonują operacje na ciągach zależne od kultury domyślnie Podaj przeciążenia metody, dzięki którym można jawnie określić kultura używana przez przekazanie <xref:System.Globalization.CultureInfo> parametru. Te przeciążenia pozwala wyeliminować kultury zmian w przypadku mapowania i sortowanie zasady i gwarantuje niezależnych od kultury.  
  
 Ta sekcja zawiera następujące tematy, aby pokazują, jak wykonać za pomocą metod .NET Framework, które są zależne od kultury operacje na ciągach niezależnych od kultury domyślnie.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wykonywanie niezależnych od kultury porównań ciągów](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Informacje dotyczące używania <xref:System.String.Compare%2A?displayProperty=nameWithType> i <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody do porównywania ciągów niezależnych od kultury.  
  
 [Wykonywanie niezależnych od kultury zmian wielkości liter](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Informacje dotyczące używania <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, i <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metod do wykonania niezależnych od kultury zmian wielkości liter.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Informacje dotyczące używania <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> i <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> wykonywanie niezależnych od kultury operacji w kolekcji.  
  
 [Wykonywanie niezależnych od kultury operacji na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Informacje dotyczące używania <xref:System.Array.Sort%2A?displayProperty=nameWithType> i <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody służące do wykonywania operacji niezależnych od kultury w tablicach.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Niezależne od kultury operacje na ciągach](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 W tym artykule opisano, dlaczego należy zwrócić uwagę kultury podczas wykonywania operacji na ciągach i zawiera wskazówki dotyczące przeprowadzania zależne od kultury operacji i przeprowadzania operacji niezależnych od kultury.
