---
title: Private Protected
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 265141f77f4a61a61414a07214830feaa8a1ab05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351345"
---
# <a name="private-protected-visual-basic"></a>Prywatna chroniona (Visual Basic)

Kombinacja słowa kluczowego `Private Protected` jest modyfikatorem dostępu składowej. Członek `Private Protected` jest dostępny dla wszystkich elementów członkowskich w klasie zawierającej, a także typów pochodzących od klasy zawierającej, ale tylko wtedy, gdy znajdują się w jego zestawie zawierającym.

Można określić `Private Protected` tylko dla elementów członkowskich klasy; nie można zastosować `Private Protected` do elementów członkowskich struktury, ponieważ struktury nie mogą być dziedziczone.

Modyfikator dostępu `Private Protected` jest obsługiwany przez Visual Basic 15,5 i nowsze. Aby go użyć, można dodać następujący element do pliku projektu Visual Basic (\*. vbproj). Tak długo, jak Visual Basic 15,5 lub nowszy jest zainstalowany w systemie, umożliwia korzystanie ze wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji [, zobacz Ustawianie wersji językowej Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> W programie Visual Studio wybierz pozycję Pomoc F1 na `private protected` zawiera pomoc dla opcji [Private](private.md) lub [Protected](protected.md). IDE wybiera pojedynczy token w obszarze kursora zamiast słowa złożonego.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** `Private Protected` można używać tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla elementu `Protected` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** Cały kod w klasie ma dostęp do jego elementów. Kod w dowolnej klasie, która dziedziczy z klasy bazowej i znajduje się w tym samym zestawie, może uzyskać dostęp do wszystkich elementów `Private Protected` klasy bazowej. Jednak kod w dowolnej klasie, która dziedziczy z klasy bazowej i jest zawarty w innym zestawie, nie może uzyskać dostępu do klasy bazowej `Private Protected` elementów.

- **Modyfikatory dostępu.** Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Modyfikator `Private Protected` może być używany w tych kontekstach:

- [Instrukcja klasy](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżonej

- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegata — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie

- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Instrukcja enum](../../../visual-basic/language-reference/statements/enum-statement.md) wyliczenia zagnieżdżona w klasie

- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)

- [Instrukcja interfejsu](../../../visual-basic/language-reference/statements/interface-statement.md) w interfejsie zagnieżdżonym w klasie

- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)

- [Instrukcja struktury](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżonej w klasie

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Zobacz także

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
