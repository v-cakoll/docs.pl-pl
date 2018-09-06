---
title: Nazwy identyfikatorów
description: Dowiedz się, zasady dotyczące nazw prawidłowym identyfikatorem języka programowania C#.
ms.date: 08/21/2018
ms.openlocfilehash: e5ff83661c9a86273760f32a795f7de6dbc7bf1d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877888"
---
# <a name="identifier-names"></a>Nazwy identyfikatorów

**Identyfikator** nazywa się przypisać do elementu członkowskiego (klasy, interfejsu, struktury, delegata lub typu wyliczeniowego), typ, zmienna lub przestrzeni nazw. Ważne identyfikatory muszą wykonać następujące czynności:

- Identyfikatory musi rozpoczynać się od litery, lub `_`.
- Identyfikatory mogą zawierać znaki Unicode, znaki cyfr dziesiętnych, łączenie znaków Unicode, łączenie znaków Unicode lub formatowanie znaków Unicode. Aby uzyskać więcej informacji na temat kategorii Unicode, zobacz [baza danych kategorii Unicode](https://www.unicode.org/reports/tr44/).
Można zadeklarować identyfikatory, które odpowiadają słowa kluczowe języka C# za pomocą `@` prefiks identyfikatora. `@` Nie jest częścią nazwy identyfikatora. Na przykład `@if` deklaruje identyfikatora o nazwie `if`. Te [verbatim identyfikatory](../../language-reference/tokens/verbatim.md) są głównie do współdziałania z identyfikatorów zdeklarowanych w innych językach.

Aby uzyskać pełną definicję prawidłowych identyfikatorów, zobacz [temat identyfikatory w specyfikacji języka C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Konwencje nazewnictwa

Oprócz reguł, istnieje kilka identyfikatora [konwencje nazewnictwa](../../../standard/design-guidelines/naming-guidelines.md) używane w całym interfejsów API platformy .NET. Zgodnie z Konwencją, C# programy użyj `PascalCase` dla nazwy typu, przestrzeni nazw i wszystkie publiczne elementy członkowskie. Ponadto następujące konwencje są wspólne:

- Interfejs nazw rozpoczyna się od wielkiej litery `I`.
- Atrybut typy kończących się wyrazem `Attribute`.
- Typach wyliczeniowych na użytek pojedynczej rzeczownik bez flag i liczba mnoga rzeczownik flag.
- Identyfikatory nie powinny zawierać dwóch kolejnych `_` znaków. Te nazwy są zarezerwowane dla identyfikatorów wygenerowanego przez kompilator.

## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Konstrukcja programu C#](../inside-a-program/index.md)
- [Dokumentacja języka C#](../../language-reference/index.md)
- [Klasy](../classes-and-structs/classes.md)
- [Struktury](../classes-and-structs/structs.md)
- [Przestrzenie nazw](../namespaces/index.md)
- [Interfejsy](../interfaces/index.md)
- [Delegaci](../delegates/index.md)
