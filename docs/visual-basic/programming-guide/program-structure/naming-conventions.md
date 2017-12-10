---
title: "Visual Basic — Konwencje nazewnictwa"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dfdb403519d7e29602fc87445ce32aeb0e55250e
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="visual-basic-naming-conventions"></a>Visual Basic — Konwencje nazewnictwa
Po nadaniu nazwy elementu w aplikacji Visual Basic, pierwszym znakiem tej nazwy musi być literą lub znakiem podkreślenia. Należy jednak pamiętać, że nazwy rozpoczynające się od znaku podkreślenia. nie są zgodne z [niezależność od języka i elementy niezależne od języka](../../../../docs/standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS).  
  
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
 [Słowa kluczowe jako nazwy elementów w Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)
