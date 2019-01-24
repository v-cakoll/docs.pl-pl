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
ms.openlocfilehash: ebb9d21e32993f2eb035993d32dc3de7d97b49f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672139"
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic — Konwencje nazewnictwa
Nazwa elementu w aplikacji Visual Basic, musi być pierwszym znakiem tej nazwy, litery alfabetu lub znaku podkreślenia. Należy jednak pamiętać, że nazwy rozpoczynające się od znaku podkreślenia nie są zgodne z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Poniższe sugestie dotyczą nazewnictwa.  
  
-   Rozpoczęcie każdego wyrazu oddzielne nazwę wielką literą, podobnie jak w `FindLastRecord` i `RedrawMyForm`.  
  
-   Rozpocznij nazwy funkcji i metody z zlecenie, podobnie jak w `InitNameArray` lub `CloseDialog`.  
  
-   Rozpocznij klasy, struktury, moduł i nazwy właściwości zawierające rzeczownik, podobnie jak w `EmployeeName` lub `CarAccessory`.  
  
-   Rozpocznij interfejsu nazw z prefiksem "I", następuje rzeczownik lub frazy rzeczownik, takie jak `IComponent`, lub przymiotnikiem, opisujący zachowanie interfejsu, takie jak `IPersistable`. Nie używać znaku podkreślenia i skróty oszczędnie, ponieważ skróty może spowodować błąd.  
  
-   Nazwy programów obsługi zdarzeń zaczynać się od opisujące typ zdarzenia następuje rzeczownik "`EventHandler`"sufiksu, jak w"`MouseEventHandler`".  
  
-   W polu nazwy klas argument zdarzeń zawierają "`EventArgs`" sufiks.  
  
-   Jeśli zdarzenie utworzono według koncepcji "before" lub "after", użyj przyrostka, w chwili obecnej czasu teraźniejszego lub przeszłego, podobnie jak w "`ControlAdd`"or"`ControlAdded`".  
  
-   Długa lub często używanych terminów Użyj skrótów zapewnienie długości nazwy rozsądne, na przykład, "HTML", a nie "Formacie HTML". Ogólnie rzecz biorąc nazwy zmiennych, które są większe niż 32 znaki są trudne do odczytania na monitorze równa niskiej rozdzielczości. Ponadto upewnij się, że Twoje skróty są spójne w całej aplikacji. Losowo przełączania w projekcie między "HTML" i "Formacie HTML" można wprowadzać w błąd.  
  
-   Unikaj używania nazw w zakresie wewnętrznym, które są takie same jak nazwy w zewnętrznym zakresie. Jeśli problem wchodzisz, mogą wystąpić błędy. Jeśli występuje konflikt między zmienną i słowo kluczowe o takiej samej nazwie, należy określić słowo kluczowe, poprzedzając je za pomocą biblioteki odpowiedniego typu. Na przykład, jeśli masz zmienną o nazwie `Date`, można użyć wewnętrznego `Date` funkcji tylko przez wywołanie metody <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także
- [Słowa kluczowe jako nazwy elementów w kodzie](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
