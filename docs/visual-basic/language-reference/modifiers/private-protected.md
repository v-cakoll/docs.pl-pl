---
title: Prywatne chronione (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>Prywatne chronione (Visual Basic)

`Private Protected` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego. A `Private Protected` element członkowski jest dostępny na wszystkich elementów członkowskich w zawierająca go klasa, a także typy pochodzące od klasy zawierające, ale tylko wtedy, gdy występują w zawierający go zestaw. 

Można określić `Private Protected` tylko w elementach członkowskich klas; nie można zastosować `Private Protected` do elementów członkowskich struktury ponieważ struktur nie może być dziedziczona.

`Private Protected` Modyfikator dostępu jest obsługiwane przez 15,5 cala Visual Basic i nowszych. Aby go użyć, można dodać następującego elementu w pliku projektu (*.vbproj) języka Visual Basic. Jak długo jako 15,5 cala Visual Basic lub nowszy jest zainstalowany w systemie, umożliwia ona korzystać z funkcji języka obsługiwane w najnowszej wersji kompilatora Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> W programie Visual Studio, wybierając pomocy F1 w `private protected` zawiera informacje pomocne w obu [prywatnej](private.md) lub [chronione](protected.md). IDE wybiera jeden token pod kursorem zamiast wyraz złożony.

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można użyć `Private Protected` tylko na poziomie klasy. Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** Cały kod w klasie mogą uzyskiwać dostęp do swoich elementów. Kod w dowolnej klasy, która pochodzi z klasy podstawowej i znajduje się w tym samym zestawie mogą uzyskać dostęp do wszystkich `Private Protected` elementy klasy podstawowej. Jednak kod w dowolnej klasy, która pochodzi z klasy podstawowej i jest zawarty w innym zestawie nie ma dostępu do klasy podstawowej `Private Protected` elementów.

- **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*. Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).
  
 `Private Protected` Modyfikatora można używać w tych sytuacjach:  
  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md) klasy zagnieżdżone  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md) delegata zagnieżdżona w klasie  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md) z eumeration zagnieżdżona w klasie 
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md) interfejsu zagnieżdżona w klasie 
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Struktura instrukcji](../../../visual-basic/language-reference/statements/structure-statement.md) struktury zagnieżdżone w klasie 
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Friend chronionych](./protected-friend.md)   
[Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
