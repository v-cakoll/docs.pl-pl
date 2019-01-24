---
title: Prywatny chroniony (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 70f725712d52ad055ff69046096da10b8edfb67c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701147"
---
# <a name="private-protected-visual-basic"></a>Prywatny chroniony (Visual Basic)

`Private Protected` Kombinacja słów kluczowych jest modyfikator dostępu składowej. A `Private Protected` element członkowski jest dostępna, wszystkie elementy członkowskie w swojej klasie zawierający, a także typów pochodnych typu zawierającego klasy, ale tylko wtedy, gdy występują w jego zawierające zestaw. 

Można określić `Private Protected` tylko na składowych klas; nie można zastosować `Private Protected` do elementów członkowskich struktury ponieważ struktury nie może być dziedziczona.

`Private Protected` Modyfikator dostępu jest obsługiwane w wersji 15.5 programu Visual Basic lub nowszy. Aby go użyć, można dodać następującego elementu do projektu języka Visual Basic (\*.vbproj) pliku. Jak długo, jak 15.5 Visual Basic lub nowszy jest zainstalowany w systemie, umożliwia korzystanie z zalet wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora języka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../language-reference/configure-language-version.md).

> [!NOTE]
> W programie Visual Studio, wybierając opcję pomocy F1 na `private protected` zapewnia pomoc dla dowolnego [prywatnej](private.md) lub [chronione](protected.md). Środowisko IDE wybiera jednego tokenu pod kursorem, a nie jako wyraz złożony.

## <a name="rules"></a>reguły

- **Kontekst deklaracji.** Możesz użyć `Private Protected` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** Cały kod w klasie mogą uzyskać dostęp do jego elementów. Kod w każdej klasy, która pochodzi z klasy bazowej i jest zawarty w tym samym zestawie mogą uzyskać dostęp do wszystkich `Private Protected` elementów klasy bazowej. Jednak kod w każdej klasy, która pochodzi z klasy bazowej i znajduje się w innym zestawie nie może uzyskiwać dostęp do klasy bazowej `Private Protected` elementów.

- **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*. Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 `Private Protected` Modyfikator mogą być używane w tych kontekstach:  
  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżonej  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration zagnieżdżona w klasie 
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md) interfejsu zagnieżdżona w klasie 
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Struktury instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżona w klasie 
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Protected Friend](./protected-friend.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
