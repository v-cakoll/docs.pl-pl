---
title: Nazwy identyfikatorów
description: Poznaj reguły dotyczące prawidłowych nazw identyfikatorów w języku programowania Języka C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673371"
---
# <a name="identifier-names"></a>Nazwy identyfikatorów

Identyfikator **identifier** to nazwa przypisana do typu (klasa, interfejs, struktura, delegat lub wyliczenie), element członkowski, zmienna lub obszar nazw. Prawidłowe identyfikatory muszą być zgodne z następującymi zasadami:

- Identyfikatory muszą zaczynać się `_`od litery lub .
- Identyfikatory mogą zawierać znaki literunicode, znaki cyfr dziesiętnych, znaki łączące Unicode, znaki unicode łączące znaki lub znaki formatowania Unicode. Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [bazę danych kategorii Unicode](https://www.unicode.org/reports/tr44/).
Można zadeklarować identyfikatory, które pasują do `@` słów kluczowych Języka C#, używając prefiksu na identyfikatorze. Nie `@` jest częścią nazwy identyfikatora. Na przykład `@if` deklaruje identyfikator o `if`nazwie . Te [dosłowne identyfikatory](../../language-reference/tokens/verbatim.md) są przede wszystkim dla interoperacyjności z identyfikatorami zadeklarowanymi w innych językach.

Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat Identyfikatory w specyfikacji języka języka Języka C#.](../../../../_csharplang/spec/lexical-structure.md#identifiers)

## <a name="naming-conventions"></a>Konwencje nazewnictwa

Oprócz reguł istnieje wiele [konwencji nazewnictwa identyfikatorużywanych](../../../standard/design-guidelines/naming-guidelines.md) w interfejsach API .NET. Zgodnie z konwencją programy `PascalCase` Języka C# są używane dla nazw typów, przestrzeni nazw i wszystkich publicznych elementów członkowskich. Ponadto wspólne są następujące konwencje:

- Nazwy interfejsów zaczynają `I`się od kapitału .
- Typy atrybutów kończą `Attribute`się słowem .
- Typy wyliczenia używają rzeczownika liczby pojedynczej dla innych niż flagi i rzeczownika liczby mnogiej dla flag.
- Identyfikatory nie powinny `_` zawierać dwóch kolejnych znaków. Nazwy te są zarezerwowane dla identyfikatorów generowanych przez kompilator.

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Konstrukcja programu C#](./index.md)
- [Odwołanie do języka C#](../../language-reference/index.md)
- [Klasy](../classes-and-structs/classes.md)
- [Typy konstrukcji](../../language-reference/builtin-types/struct.md)
- [Przestrzenie nazw](../namespaces/index.md)
- [Interfejsy](../interfaces/index.md)
- [Delegaty](../delegates/index.md)
