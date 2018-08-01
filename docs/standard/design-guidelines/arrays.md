---
title: Tablice
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2945ead7c22b759ce88f6585e2254e9bc540a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570407"
---
# <a name="arrays"></a>Tablice
**✓ DO** preferowane przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API. [Kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) sekcja zawiera szczegółowe informacje o tym, jak wybranie kolekcji i tablic.  
  
 **X DO NOT** użyć pola tablicy tylko do odczytu. Samo pole jest tylko do odczytu i nie można zmienić, ale można zmienić elementów w tablicy.  
  
 **✓ CONSIDER** za pomocą Tablice nieregularne zamiast wielowymiarowych tablic.  
  
 Nieregularna tablica jest tablicą z elementami, które są również tablic. Tablice, które tworzą elementów może mieć różne rozmiary, co może prowadzić do mniej utracona dla niektórych zestawów danych (np. macierz rozrzedzone) w porównaniu do tablic wielowymiarowych. Ponadto CLR optymalizuje operacje na indeksie na Tablice nieregularne tak może charakteryzują się lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
