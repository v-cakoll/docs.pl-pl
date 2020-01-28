---
title: Tablice
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741808"
---
# <a name="arrays"></a>Tablice
✔️ Preferuj przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API. Sekcja [kolekcje](../../../docs/standard/design-guidelines/guidelines-for-collections.md) zawiera szczegółowe informacje dotyczące wyboru między kolekcjami i tablicami.

 ❌ nie używaj pól tablicy tylko do odczytu. Samo pole jest tylko do odczytu i nie można go zmienić, ale elementy w tablicy można zmienić.

 ✔️ ROZWAŻYĆ użycie tablic nieregularnych zamiast tablic wielowymiarowych.

 Tablica nieregularna jest tablicą zawierającą elementy, które są również tablicami. Tablice wchodzące w skład elementów mogą mieć różne rozmiary, co prowadzi do mniejszej ilości wolnego miejsca dla niektórych zestawów danych (np. macierzy rozrzedzonych) w porównaniu do tablic wielowymiarowych. Ponadto środowisko CLR optymalizuje operacje indeksowania w tablicach nieregularnych, dzięki czemu mogą one mieć lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
