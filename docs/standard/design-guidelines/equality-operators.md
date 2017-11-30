---
title: "Operatory równości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a>Operatory równości
W tej sekcji omówiono przeciążania Operatory równości i odwołuje się do `operator==` i `operator!=` jako operatory równości.  
  
 **X nie** jedną Operatory równości i nie inne przeciążenia.  
  
 **CZY ✓** upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory porównania ma dokładnie tej samej semantyki i podobne charakterystyki wydajności.  
  
 Często oznacza to, że `Object.Equals` musi zostać zastąpiona, gdy są przeciążone operatory równości.  
  
 **X należy UNIKAĆ** zgłaszanie wyjątków z Operatory równości.  
  
 Na przykład zwróci wartość false, jeśli jeden z argumentów ma wartość null zamiast zgłaszanie `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operatory równości dla typów wartości  
 **CZY ✓** przeciążać Operatory równości w typach wartości, jeśli równości jest łatwy do rozpoznania.  
  
 W większości języków programowania, nie ma żadnych domyślną implementację `operator==` dla typów wartości.  
  
## <a name="equality-operators-on-reference-types"></a>Operatory równości w typach referencyjnych  
 **X należy UNIKAĆ** przeładowanie operatorów równości w typach referencyjnych.  
  
 Wiele języków ma operatory wbudowanych równości dla typów odwołań. Wbudowane Operatorzy zazwyczaj zaimplementować równości odwołań, a wielu deweloperów są zaskoczeniem, w przypadku zmiany domyślnego zachowania na równości wartości.  
  
 Ten problem jest skorygowane dla typów odwołań niezmienne, ponieważ immutability utrudnia znacznie należy zauważyć różnicę między równości odwołań i o równość wartości.  
  
 **X należy UNIKAĆ** przeładowanie operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż w przypadku równości odwołań.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące użycia](../../../docs/standard/design-guidelines/usage-guidelines.md)
