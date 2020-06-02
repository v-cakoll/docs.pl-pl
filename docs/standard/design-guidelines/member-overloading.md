---
title: Przeciążanie składowej
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: 6a2cd6d4dd293a7f4a408e1ee97a125c9454be41
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289008"
---
# <a name="member-overloading"></a>Przeciążanie składowej
Przeciążenie elementu członkowskiego oznacza utworzenie dwóch lub większej liczby elementów członkowskich tego samego typu, które różnią się tylko liczbą lub typem parametrów, ale mają tę samą nazwę. Na przykład w poniższym przykładzie `WriteLine` Metoda jest przeciążona:

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 Ponieważ tylko metody, konstruktory i właściwości indeksowane mogą mieć parametry, tylko te elementy członkowskie mogą być przeciążone.

 Przeciążanie to jedna z najważniejszych technik zwiększania użyteczności, produktywności i czytelności bibliotek wielokrotnego użytku. Przeciążanie liczby parametrów pozwala na zapewnienie prostszej wersji konstruktorów i metod. Przeciążanie w typie parametru umożliwia używanie tej samej nazwy elementu członkowskiego dla elementów członkowskich wykonujących identyczne operacje na wybranym zestawie różnych typów.

 ✔️ Spróbuj użyć opisowych nazw parametrów, aby wskazać wartość domyślną używaną przez krótsze przeciążenia.

 ❌UNIKAj arbitralnie różnych nazw parametrów w przeciążeniach. Jeśli parametr w jednym przeciążeniu reprezentuje takie samo dane wejściowe jak parametr w innym przeciążeniu, parametry powinny mieć taką samą nazwę.

 ❌UNIKAj niespójności w kolejności parametrów w przeciążonych elementach członkowskich. Parametry o tej samej nazwie powinny znajdować się w tej samej pozycji we wszystkich przeciążeń.

 ✔️ WYKONAĆ tylko najdłuższym wirtualnym przeciążeniem (jeśli jest wymagana rozszerzalność). Krótsze przeciążenia powinny po prostu wywołać do dłuższego przeciążenia.

 ❌NIE należy używać `ref` `out` modyfikatorów ani do przeciążania elementów członkowskich.

 Niektóre języki nie mogą rozpoznawać wywołań do przeciążenia, takich jak ten. Ponadto takie przeciążenia zwykle mają całkowicie inną semantykę i prawdopodobnie nie powinny być przeciążeniami, ale zamiast nich należy użyć dwóch oddzielnych metod.

 ❌NIE należy przeciążać z parametrami w tym samym położeniu i podobnych typach z inną semantyką.

 ✔️ zezwalać na `null` przekazywanie argumentów opcjonalnych.

 ✔️ użyć przeciążenia elementu członkowskiego zamiast definiować członków z argumentami domyślnymi.

 Argumenty domyślne nie są zgodne ze specyfikacją CLS.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
