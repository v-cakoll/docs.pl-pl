---
title: Projekt struktury
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: c6ac53014e048da3a90dd7b8e961176f61e90355
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290814"
---
# <a name="struct-design"></a>Projekt struktury
Typ wartości ogólnego przeznaczenia jest najczęściej określany jako struktura, jego słowo kluczowe języka C#. Ta sekcja zawiera wskazówki dotyczące ogólnego projektowania struktury.

 ❌Nie udostępniaj konstruktora bez parametrów dla struktury.

 Poniższe wytyczne umożliwiają tworzenie tablic struktur bez konieczności uruchamiania konstruktora dla każdego elementu tablicy. Należy zauważyć, że w języku C# nie jest dozwolone, aby struktury miały konstruktory bez parametrów.

 ❌NIE Definiuj modyfikowalnych typów wartościowych.

 Modyfikowalne typy wartości mają kilka problemów. Na przykład, gdy metoda pobierająca Właściwość zwraca typ wartości, wywołujący otrzymuje kopię. Ponieważ kopia jest tworzona niejawnie, deweloperzy mogą nie wiedzieć, że są one mutacją, a nie pierwotną wartością. Ponadto w niektórych językach (w szczególności Języki dynamiczne) występują problemy z użyciem modyfikowalnych typów wartości, ponieważ nawet zmienne lokalne, gdy jest używana, powoduje, że kopia zostanie wykonana.

 ✔️ Upewnij się, że stan, w którym wszystkie dane wystąpienia są ustawione na wartość zero, wartość false lub wartość null (odpowiednio), jest prawidłowy.

 Zapobiega to przypadkowemu tworzeniu nieprawidłowych wystąpień podczas tworzenia tablicy struktur.

 ✔️ Implementowanie <xref:System.IEquatable%601> w typach wartości.

 <xref:System.Object.Equals%2A?displayProperty=nameWithType>Metoda w typach wartości powoduje opakowanie, a jej domyślna implementacja nie jest bardzo wydajna, ponieważ używa odbicia. <xref:System.IEquatable%601.Equals%2A>może mieć znacznie lepszą wydajność i można go zaimplementować, aby nie powodowały opakowywania opakowania.

 ❌NIE należy jawnie zwiększać <xref:System.ValueType> . W rzeczywistości większość języków zapobiega tym.

 Ogólnie rzecz biorąc, struktury mogą być bardzo przydatne, ale powinny być używane tylko w przypadku małych, pojedynczych, niezmiennych wartości, które nie będą często opakowane.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania typów](type.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wybieranie między klasą i strukturą](choosing-between-class-and-struct.md)
