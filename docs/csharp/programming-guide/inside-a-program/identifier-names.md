---
title: Nazwy identyfikatorów
description: Poznaj reguły dotyczące prawidłowych nazw identyfikatorów w języku C# programowania.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589357"
---
# <a name="identifier-names"></a>Nazwy identyfikatorów

**Identyfikator** to nazwa przypisywana do typu (Klasa, interfejs, struktura, delegat lub enum), element członkowski, zmienna lub przestrzeń nazw. Prawidłowe identyfikatory muszą być zgodne z następującymi regułami:

- Identyfikatory muszą zaczynać się literą lub `_`.
- Identyfikatory mogą zawierać znaki Unicode, cyfry dziesiętne, znaki łączące kod Unicode, znaki łączące kod Unicode lub znaki formatowania Unicode. Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [baza danych kategorii Unicode](https://www.unicode.org/reports/tr44/).
Identyfikatory, które pasują C# do słów kluczowych, można `@` zadeklarować przy użyciu prefiksu identyfikatora. Nie `@` jest częścią nazwy identyfikatora. Na przykład `@if` deklaruje identyfikator o nazwie `if`. Te [identyfikatory Verbatim](../../language-reference/tokens/verbatim.md) są głównie do współdziałania z identyfikatorami zadeklarowanymi w innych językach.

Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat identyfikatory w C# specyfikacji języka](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Konwencje nazewnictwa

Oprócz reguł istnieje wiele [konwencji nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) identyfikatorów używanych w ramach interfejsów API platformy .NET. Zgodnie z Konwencją C# programy `PascalCase` programu korzystają z nazw typów, przestrzeni nazw i wszystkich publicznych członków. Ponadto są wspólne następujące konwencje:

- Nazwy interfejsów zaczynają się od `I`wielkiej litery.
- Typy atrybutów kończą się słowem `Attribute`.
- Typy wyliczeniowe używają pojedynczej rzeczownika dla flag innych niż flagi i rzeczownika w liczbie mnogiej dla flag.
- Identyfikatory nie powinny zawierać dwóch następujących `_` po sobie znaków. Te nazwy są zarezerwowane dla identyfikatorów wygenerowanych przez kompilator.

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Konstrukcja programu C#](./index.md)
- [Dokumentacja języka C#](../../language-reference/index.md)
- [Klasy](../classes-and-structs/classes.md)
- [Struktury](../classes-and-structs/structs.md)
- [Przestrzenie nazw](../namespaces/index.md)
- [Interfejsy](../interfaces/index.md)
- [Delegaty](../delegates/index.md)
