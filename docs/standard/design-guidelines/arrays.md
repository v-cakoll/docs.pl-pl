---
title: Tablice
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: 30277507050091de6b1e9293401d61ac5e351a1f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280624"
---
# <a name="arrays"></a>Tablice
✔️ Preferuj przy użyciu kolekcji za pośrednictwem tablic w publicznych interfejsach API. Sekcja [kolekcje](guidelines-for-collections.md) zawiera szczegółowe informacje dotyczące wyboru między kolekcjami i tablicami.

 ❌NIE używaj pól tablicy tylko do odczytu. Samo pole jest tylko do odczytu i nie można go zmienić, ale elementy w tablicy można zmienić.

 ✔️ ROZWAŻYĆ użycie tablic nieregularnych zamiast tablic wielowymiarowych.

 Tablica nieregularna jest tablicą zawierającą elementy, które są również tablicami. Tablice wchodzące w skład elementów mogą mieć różne rozmiary, co prowadzi do mniejszej ilości wolnego miejsca dla niektórych zestawów danych (np. macierzy rozrzedzonych) w porównaniu do tablic wielowymiarowych. Ponadto środowisko CLR optymalizuje operacje indeksowania w tablicach nieregularnych, dzięki czemu mogą one mieć lepszą wydajność środowiska uruchomieniowego w niektórych scenariuszach.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące użycia](usage-guidelines.md)
