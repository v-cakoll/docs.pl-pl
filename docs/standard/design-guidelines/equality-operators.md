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
ms.openlocfilehash: 31a5ce18f4526b5e3b8411365dff812601de87ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709442"
---
# <a name="equality-operators"></a>Operatory równości
W tej sekcji omówiono przeciążanie operatorów równości i odwołuje się do `operator==` i `operator!=` jako operatory równości.  
  
 **X DO NOT** jedną Operatory równości i nie inne przeciążenia.  
  
 **✓ DO** upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory porównania ma dokładnie tej samej semantyki i podobne charakterystyki wydajności.  
  
 Często oznacza to, że `Object.Equals` należy przesłonić, gdy operatory równości są przeciążone.  
  
 **X AVOID** zgłaszanie wyjątków z Operatory równości.  
  
 Na przykład Zwróć wartość false, jeśli jeden z argumentów ma wartość null zamiast zgłaszać `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Operatory równości w typach wartości  
 **✓ DO** przeciążać Operatory równości w typach wartości, jeśli równości jest łatwy do rozpoznania.  
  
 W większości języków programowania nie istnieje domyślna implementacja `operator==` dla typów wartości.  
  
## <a name="equality-operators-on-reference-types"></a>Operatory równości w typach referencyjnych  
 **X AVOID** przeładowanie operatorów równości w typach referencyjnych.  
  
 Wiele języków ma wbudowane operatory równości dla typów referencyjnych. Operatory wbudowane zwykle implementują równość odwołań, a wielu deweloperów jest przeważnie, gdy domyślne zachowanie zostanie zmienione na równość wartości.  
  
 Ten problem został skorygowany dla niezmiennego typu referencyjnego, ponieważ niezmienności znacznie trudniejsze do zauważenia różnicy między równośćmi referencyjnymi i równość wartości.  
  
 **X AVOID** przeładowanie operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż w przypadku równości odwołań.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
