---
title: Projekt konstruktora
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400604"
---
# <a name="constructor-design"></a>Projekt konstruktora

Istnieją dwa rodzaje konstruktorów: konstruktory typu i konstruktory wystąpienia.

Konstruktory typu są statyczne i są uruchamiane przez CLR przed typem jest używany. Konstruktory wystąpienia są uruchamiane po utworzeniu wystąpienia typu.

Konstruktory typu nie mogą przyjmować żadnych parametrów. Konstruktory wystąpienia może. Konstruktory wystąpienia, które nie przyjmują żadnych parametrów są często nazywane konstruktorów bezparametrów.

Konstruktory są najbardziej naturalny sposób tworzenia wystąpień typu. Większość deweloperów będzie wyszukiwać i próbować użyć konstruktora, zanim rozważyalternatywne sposoby tworzenia wystąpień (takich jak metody fabryczne).

✔️ ROZWAŻ zapewnienie prostych, najlepiej domyślnych konstruktorów.

Prosty konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są prymitywami lub wyliczeniami. Takie proste konstruktory zwiększają użyteczność struktury.

✔️ ZASTANÓW SIĘ przy użyciu statycznej metody fabryki zamiast konstruktora, jeśli semantyka żądanej operacji nie mapuje bezpośrednio do budowy nowego wystąpienia lub jeśli zgodnie z wytycznymi projektowymi konstruktora czuje się nienaturalne.

✔️ UŻYWAĆ parametrów konstruktora jako skrótów do ustawiania właściwości głównych.

Nie powinno być żadnej różnicy w semantyce między użyciem pustego konstruktora, a następnie niektóre zestawy właściwości i przy użyciu konstruktora z wieloma argumentami.

✔️ należy użyć tej samej nazwy dla parametrów konstruktora i właściwości, jeśli parametry konstruktora są używane do prostego ustawienia właściwości.

Jedyną różnicą między takimi parametrami a właściwościami powinna być obudowa.

✔️ zrobić minimalną pracę w konstruktorze.

Konstruktory nie należy wykonywać wiele pracy innych niż przechwytywanie parametrów konstruktora. Koszt każdego innego przetwarzania powinien być opóźniony do momentu, gdy będzie to wymagane.

✔️ do zgłaszać wyjątki od konstruktorów instancji, jeśli jest to właściwe.

✔️ do jawnie zadeklarować konstruktora parametrów publicznych w klasach, jeśli taki konstruktor jest wymagany.

Jeśli nie jawnie zadeklarować żadnych konstruktorów na typ, wiele języków (takich jak C#) automatycznie doda konstruktora public parameterless. (Klasy abstrakcyjne uzyskać chroniony konstruktora.)

Dodanie konstruktora sparametryzowanego do klasy uniemożliwia kompilatorowi dodawanie konstruktora bezparametrowego. Często powoduje to przypadkowe zmiany.

❌UNIKAJ jawnie definiowania konstruktorów bezparametrów na strukturach.

Dzięki temu tworzenie tablicy szybciej, ponieważ jeśli konstruktor bezparametrów nie jest zdefiniowany, nie musi być uruchamiany na każdym gnieździe w tablicy. Należy zauważyć, że wiele kompilatorów, w tym C#, nie zezwalają structs mieć konstruktorów bezparametrów z tego powodu.

❌UNIKAJ wywoływania wirtualnych elementów członkowskich na obiekcie wewnątrz jego konstruktora.

Wywołanie elementu członkowskiego wirtualnego spowoduje, że najbardziej pochodne zastąpić być wywoływane, nawet jeśli konstruktor typu najbardziej pochodnych nie został jeszcze w pełni uruchomiony.

## <a name="type-constructor-guidelines"></a>Wskazówki dotyczące konstruktora tekstu

✔️ zrobić statyczne konstruktory prywatne.

Konstruktora statycznego, zwany także konstruktora klasy, jest używany do inicjowania typu. CLR wywołuje konstruktora statycznego przed pierwszym wystąpieniem typu jest tworzony lub wszystkie elementy statyczne na tym typie są wywoływane. Użytkownik nie ma kontroli nad, gdy konstruktor statyczny jest wywoływana. Jeśli konstruktor statyczny nie jest prywatny, może być wywoływany przez kod inny niż CLR. W zależności od operacji wykonywanych w konstruktorze może to spowodować nieoczekiwane zachowanie. Kompilator C# wymusza konstruktory statyczne jako prywatne.

❌NIE zgłaszaj wyjątków od konstruktorów statycznych.

Jeśli wyjątek jest generowany z konstruktora typu, typ nie jest użyteczny w bieżącej domenie aplikacji.

✔️ NALEŻY WZIĄĆ POD UWAGĘ inicjowanie pól statycznych w wierszu, a nie jawnie przy użyciu konstruktorów statycznych, ponieważ czas wykonywania jest w stanie zoptymalizować wydajność typów, które nie mają jawnie zdefiniowane static konstruktora.

*Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

*Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*

## <a name="see-also"></a>Zobacz też

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
