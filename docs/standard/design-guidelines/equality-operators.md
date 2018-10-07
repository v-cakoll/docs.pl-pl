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
ms.openlocfilehash: 27550a8fd8292029cad9c2e699374a190b1a532e
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839358"
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
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
