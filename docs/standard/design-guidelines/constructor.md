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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741738"
---
# <a name="constructor-design"></a>Projekt konstruktora

Istnieją dwa rodzaje konstruktorów: konstruktory typów i konstruktory wystąpień.

Konstruktory typów są statyczne i są uruchamiane przez środowisko CLR przed użyciem typu. Konstruktory wystąpień są uruchamiane podczas tworzenia wystąpienia typu.

Konstruktory typów nie mogą przyjmować żadnych parametrów. Konstruktory wystąpień mogą. Konstruktory wystąpień, które nie przyjmują żadnych parametrów, są często nazywane konstruktorami bez parametrów.

Konstruktory to najbardziej naturalny sposób tworzenia wystąpień typu. Większość deweloperów przeszuka i spróbuje użyć konstruktora przed uwzględnieniem alternatywnych sposobów tworzenia wystąpień (takich jak metody fabryki).

✔️ ROZWAŻYĆ udostępnienie prostych, idealnie domyślnych konstruktorów.

Prosty Konstruktor ma bardzo małą liczbę parametrów, a wszystkie parametry są pierwotne lub wyliczeniowe. Takie proste konstruktory zwiększają użyteczność struktury.

✔️ ROZWAŻYĆ użycie statycznej metody fabryki zamiast konstruktora, Jeśli semantyka żądanej operacji nie jest mapowana bezpośrednio do konstrukcji nowego wystąpienia lub jeśli zgodnie z wytycznymi projektowania konstruktora uważać nienaturalny.

✔️ używać parametrów konstruktora jako skrótów do ustawiania właściwości głównych.

Nie powinno się różnicować semantyki między użyciem pustego konstruktora, a po nim niektóre zestawy właściwości i użycie konstruktora z wieloma argumentami.

✔️ Użyj tej samej nazwy dla parametrów konstruktora i właściwości, jeśli konstruktory są używane do zwykłego ustawiania właściwości.

Jedyną różnicą między takimi parametrami i właściwościami powinna być wielkość liter.

✔️ WYKONAĆ minimalną ilość pracy w konstruktorze.

Konstruktory nie powinny wykonywać wielu zadań niż przechwycić parametry konstruktora. Koszt dowolnego innego przetwarzania powinien zostać opóźniony do czasu wymagane.

✔️ należy zgłosić wyjątki z konstruktorów wystąpień, jeśli są odpowiednie.

✔️ jawnie zadeklarować publiczny Konstruktor bez parametrów w klasach, jeśli taki Konstruktor jest wymagany.

Jeśli nie deklarujesz jawnie żadnych konstruktorów w typie, wiele języków (takich jak C#) automatycznie doda publiczny Konstruktor bez parametrów. (Klasy abstrakcyjne uzyskują chroniony Konstruktor).

Dodanie konstruktora sparametryzowanego do klasy uniemożliwi kompilatorowi dodanie konstruktora bez parametrów. Często powoduje to przypadkowe krytyczne zmiany.

❌ UNIKAj jawnego definiowania konstruktorów bez parametrów w strukturach.

Dzięki temu tworzenie macierzy jest szybsze, ponieważ jeśli Konstruktor bez parametrów nie jest zdefiniowany, nie musi być uruchamiany w każdym gnieździe tablicy. Należy zauważyć, że wiele kompilatorów C#, w tym, nie zezwala strukturom na używanie konstruktorów bez parametrów z tego powodu.

❌ unikać wywoływania wirtualnych elementów członkowskich w obiekcie wewnątrz jego konstruktora.

Wywołanie wirtualnej składowej spowoduje wywołanie najbardziej pochodnego przesłonięcia, nawet jeśli Konstruktor najbardziej pochodnego nie został jeszcze w pełni uruchomiony.

## <a name="type-constructor-guidelines"></a>Wytyczne dotyczące konstruktora typów

✔️ uczynić statycznymi konstruktorami prywatnymi.

Konstruktor statyczny nazywany również konstruktorem klasy jest używany do inicjowania typu. CLR wywołuje konstruktora statycznego przed utworzeniem pierwszego wystąpienia typu lub wszystkie statyczne elementy członkowskie tego typu są wywoływane. Użytkownik nie ma kontroli nad tym, kiedy Konstruktor statyczny jest wywoływany. Jeśli Konstruktor statyczny nie jest prywatny, może być wywoływany przez kod inny niż CLR. W zależności od operacji wykonywanych w konstruktorze może to spowodować nieoczekiwane zachowanie. C# Kompilator wymusza, aby konstruktory statyczne były prywatne.

❌ nie zgłaszaj wyjątków od konstruktorów statycznych.

Jeśli wyjątek jest zgłaszany z konstruktora typów, typ nie jest użyteczny w bieżącej domenie aplikacji.

✔️ ROZWAŻYĆ zainicjowanie pól statycznych zamiast jawnie przy użyciu konstruktorów statycznych, ponieważ środowisko uruchomieniowe może zoptymalizować wydajność typów, które nie mają jawnie zdefiniowanego konstruktora statycznego.

*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
