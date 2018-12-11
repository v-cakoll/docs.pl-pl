---
title: Tablice
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: KrzysztofCwalina
ms.openlocfilehash: d0332591be7659aafb5b3169f92c81d47d519dc2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127566"
---
# <a name="arrays"></a>Tablice
**✓ DO** preferowane przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API. [Kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) sekcja zawiera szczegółowe informacje o tym, jak dokonać wyboru między kolekcje i tablice.  
  
 **X DO NOT** użyć pola tablicy tylko do odczytu. Samo pole jest tylko do odczytu i nie można zmienić, ale można zmienić elementy w tablicy.  
  
 **✓ CONSIDER** za pomocą Tablice nieregularne zamiast wielowymiarowych tablic.  
  
 Nieregularna tablica jest tablicy o liczbie elementów, które również są tablicami. Tablice, które tworzą elementy mogą być różne rozmiary, co zapewnia większą oszczędność miejsca dla niektórych zestawów danych (np. macierz rozrzedzone) w porównaniu do tablic wielowymiarowych. Ponadto środowisko CLR optymalizuje operacje indeksowania w Tablice nieregularne tak może charakteryzują się lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
