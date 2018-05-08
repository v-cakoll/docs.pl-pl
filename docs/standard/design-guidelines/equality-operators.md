---
title: Operatory równości
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1e5784de277d59c7bc945cbe7b605653eec7bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
