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
author: KrzysztofCwalina
ms.openlocfilehash: a43ec815275e58f4bc6462fb4f5cb4733267de31
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972113"
---
# <a name="constructor-design"></a>Projekt konstruktora

Istnieją dwa rodzaje konstruktorów: konstruktory typów i konstruktory wystąpień.

Konstruktory typów są statyczne i są uruchamiane przez środowisko CLR przed użyciem typu. Konstruktory wystąpień są uruchamiane podczas tworzenia wystąpienia typu.

Konstruktory typów nie mogą przyjmować żadnych parametrów. Konstruktory wystąpień mogą. Konstruktory wystąpień, które nie przyjmują żadnych parametrów, są często nazywane konstruktorami bez parametrów.

Konstruktory to najbardziej naturalny sposób tworzenia wystąpień typu. Większość deweloperów przeszuka i spróbuje użyć konstruktora przed uwzględnieniem alternatywnych sposobów tworzenia wystąpień (takich jak metody fabryki).

**✓ CONSIDER** udostępnia prostą, najlepiej domyślne, konstruktorów.

Prosty Konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są pierwotne lub wyliczeniowe. Takie proste konstruktory zwiększają użyteczność struktury.

**✓ CONSIDER** przy użyciu metody statycznej fabryki zamiast konstruktora semantykę Żądana operacja nie mapują bezpośrednio do tworzenia nowego wystąpienia, lub zgodnie z wytycznymi projektowania konstruktora tak nienaturalnej.

**✓ DO** parametry konstruktora jako skróty do ustawiania właściwości głównego.

Nie powinno się różnicować semantyki między użyciem pustego konstruktora, a po nim niektóre zestawy właściwości i użycie konstruktora z wieloma argumentami.

**✓ DO** Użyj takiej samej nazwy dla parametrami konstruktora a właściwością, jeśli używane są parametry konstruktora wystarczy ustawić właściwości.

Jedyną różnicą między takimi parametrami i właściwościami powinna być wielkość liter.

**✓ DO** minimalnego pracy w konstruktorze.

Konstruktory nie powinny wykonywać wielu zadań niż przechwycić parametry konstruktora. Koszt dowolnego innego przetwarzania powinien zostać opóźniony do czasu wymagane.

**✓ DO** zgłaszanie wyjątków z konstruktorów wystąpienia, w razie potrzeby.

**✓** Jawnie deklaruj publiczny Konstruktor bez parametrów w klasach, jeśli taki Konstruktor jest wymagany.

Jeśli nie deklarujesz jawnie żadnych konstruktorów w typie, wiele języków (takich jak C#) automatycznie doda publiczny Konstruktor bez parametrów. (Klasy abstrakcyjne uzyskują chroniony Konstruktor).

Dodanie konstruktora sparametryzowanego do klasy uniemożliwi kompilatorowi dodanie konstruktora bez parametrów. Często powoduje to przypadkowe krytyczne zmiany.

**X Unikaj** jawnego definiowania konstruktorów bez parametrów w strukturach.

Dzięki temu tworzenie macierzy jest szybsze, ponieważ jeśli Konstruktor bez parametrów nie jest zdefiniowany, nie musi być uruchamiany w każdym gnieździe tablicy. Należy zauważyć, że wiele kompilatorów C#, w tym, nie zezwala strukturom na używanie konstruktorów bez parametrów z tego powodu.

**X AVOID** wywoływania wirtualne elementy członkowskie dla obiekt wewnątrz jego konstruktora.

Wywołanie wirtualnej składowej spowoduje wywołanie najbardziej pochodnego przesłonięcia, nawet jeśli Konstruktor najbardziej pochodnego nie został jeszcze w pełni uruchomiony.

## <a name="type-constructor-guidelines"></a>Wytyczne dotyczące konstruktora typów

**✓ DO** Oznacz jako prywatne konstruktory statyczne.

Konstruktor statyczny nazywany również konstruktorem klasy jest używany do inicjowania typu. CLR wywołuje konstruktora statycznego przed utworzeniem pierwszego wystąpienia typu lub wszystkie statyczne elementy członkowskie tego typu są wywoływane. Użytkownik nie ma kontroli nad tym, kiedy Konstruktor statyczny jest wywoływany. Jeśli Konstruktor statyczny nie jest prywatny, może być wywoływany przez kod inny niż CLR. W zależności od operacji wykonywanych w konstruktorze może to spowodować nieoczekiwane zachowanie. C# Kompilator wymusza, aby konstruktory statyczne były prywatne.

**X DO NOT** zgłaszanie wyjątków z konstruktorów statycznych.

Jeśli wyjątek jest zgłaszany z konstruktora typów, typ nie jest użyteczny w bieżącej domenie aplikacji.

**✓ CONSIDER** inicjowanie pól statycznych zamiast jawnie konstruktory statyczne, ponieważ środowisko uruchomieniowe jest w stanie zoptymalizować wydajność typy, które nie mają jawnie zdefiniowanych Konstruktor statyczny.

*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: Konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku,](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2. wydanie przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
