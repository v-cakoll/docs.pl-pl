---
title: Operatory równości
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ae188fc7cd55dd843e93afccbe1ea05575a9c36d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129080"
---
# <a name="equality-operators"></a>Operatory równości
W tej sekcji omówiono przeciążania operacji równości operatorów i odwołuje się do `operator==` i `operator!=` jako operatory równości.  
  
 **X DO NOT** jedną Operatory równości i nie inne przeciążenia.  
  
 **✓ DO** upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory porównania ma dokładnie tej samej semantyki i podobne charakterystyki wydajności.  
  
 Często oznacza to, że `Object.Equals` musi zostać zastąpiona, gdy są przeciążone operatory równości.  
  
 **X AVOID** zgłaszanie wyjątków z Operatory równości.  
  
 Na przykład, zwróci wartość false, jeśli jeden z argumentów ma wartość null, zamiast zgłaszać `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operatory równości dla typów wartości  
 **✓ DO** przeciążać Operatory równości w typach wartości, jeśli równości jest łatwy do rozpoznania.  
  
 W większości języków programowania, jest nie domyślną implementację elementu `operator==` dla typów wartości.  
  
## <a name="equality-operators-on-reference-types"></a>Operatory równości w typach referencyjnych  
 **X AVOID** przeładowanie operatorów równości w typach referencyjnych.  
  
 Wiele języków mają wbudowane równości operatorów dla typów odwołań. Wbudowane operatory zwykle implementuje równości odwołań i wielu deweloperów są Zaskoczenie, w przypadku zmiany domyślnego zachowania na równość wartości.  
  
 Ten problem jest zmniejszany dla typów odwołań niezmienne, ponieważ niezmienności sprawia, że znacznie trudniejsze, zwróć uwagę na różnicę między równości odwołań i równości wartości.  
  
 **X AVOID** przeładowanie operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż w przypadku równości odwołań.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
