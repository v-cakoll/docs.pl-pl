---
title: Visual Basic — Konwencje nazewnictwa
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651921"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic — Konwencje nazewnictwa
Po nadaniu nazwy elementu w aplikacji Visual Basic, pierwszym znakiem tej nazwy musi być literą lub znakiem podkreślenia. Należy jednak pamiętać, że nazwy rozpoczynające się od znaku podkreślenia. nie są zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS).  
  
 Poniższe sugestie dotyczą nazewnictwa.  
  
-   Rozpocznij każdego wyrazu oddzielne w nazwie się wielką literą, podobnie jak w `FindLastRecord` i `RedrawMyForm`.  
  
-   Rozpocznij nazwy funkcji i metody z zlecenie, podobnie jak w `InitNameArray` lub `CloseDialog`.  
  
-   Rozpocznij klasy, struktury, moduł i nazwy właściwości z rzeczownik, podobnie jak w `EmployeeName` lub `CarAccessory`.  
  
-   Rozpocznij nazwy interfejs z prefiksem "I", a następnie rzeczownikiem lub frazę rzeczownik tak samo, jak `IComponent`, lub za pomocą przymiotnik tak samo, jak opisujący zachowanie interfejsu `IPersistable`. Nie używa podkreślenia i skróty oszczędnie, ponieważ skróty może spowodować ryzyko pomyłek.  
  
-   Zaczynać nazw programu obsługi zdarzeń rzeczownikiem opisujące typ zdarzenia, a następnie "`EventHandler`"sufiksu domeny, jak w"`MouseEventHandler`".  
  
-   W polu nazwy klas argument zdarzeń zawierają "`EventArgs`" sufiks.  
  
-   Jeśli zdarzenie jest pojęcie "przed" lub "po", Użyj sufiksu w chwili obecnej lub przeszłego, podobnie jak w "`ControlAdd`"lub"`ControlAdded`".  
  
-   Długie lub często używanych terminów Użyj skróty do zachowania długości nazwy uzasadnione, na przykład "kod HTML", zamiast "Formacie HTML". Ogólnie rzecz biorąc nazwy zmiennych, które są większe niż 32 znaki są trudne do odczytu na ustawioną w niskiej rozdzielczości monitora. Ponadto upewnij się, że Twoje skróty są spójne w całym całej aplikacji. Losowo przełączania w projekcie między "HTML" i "Hypertext Markup Language" może prowadzić do pomyłek.  
  
-   Należy unikać nazw w zakresie wewnętrznym, które są takie same jak nazwy w zakresie zewnętrznym. Błędy może spowodować, jeśli dostępna jest niewłaściwy zmiennej. Jeśli występuje konflikt między zmienną i słowo kluczowe o takiej samej nazwie, należy określić słowa kluczowego, poprzedzając z biblioteką odpowiedniego typu. Na przykład, jeśli masz zmiennej o nazwie `Date`, można użyć wewnętrznego `Date` funkcja tylko przez wywołanie metody <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe jako nazwy elementów w kodzie](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
