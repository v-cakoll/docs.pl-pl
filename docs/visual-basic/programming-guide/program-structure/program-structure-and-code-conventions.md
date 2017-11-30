---
title: "Struktura programu i konwencje związane z kodami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a>Struktura programu i konwencje związane z kodami (Visual Basic)
W tej sekcji przedstawiono typowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programowania struktury, udostępnia prostą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program "Hello, World", a w tym artykule omówiono [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu Konwencji. Konwencje związane z kodami są sugestie skoncentrowane nie na logice programu, ale na jego struktura fizyczna i wyglądu. Po ich ułatwia kodu do odczytu, zrozumieć i konserwacji. Konwencje związane z kodami należą między innymi:  
  
-   Standardowych formatów etykietowanie i komentarzy kodu.  
  
-   Wytyczne dotyczące odstępów, formatowanie i kod wcięcia.  
  
-   Konwencje nazewnictwa dla obiektów, zmienne i procedur.  
  
 Poniższe tematy zawierają zestaw wytyczne dotyczące programowania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy, wraz z przykładem użycia dobra.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Zawiera omówienie elementów, które tworzą [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 W tym artykule omówiono procedury, która służy jako początkowego punktu i ogólnej kontroli aplikacji.  
  
 [Referencje i Importy — instrukcja](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Omówiono sposób odwoływać się do obiektów w innych zestawów.  
  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 W tym artykule opisano, jak obszary nazw organizowanie obiektów w obrębie zestawów.  
  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Zawiera ogólne wskazówki dotyczące nazewnictwa procedur, stałe, zmienne, argumentów i obiektów.  
  
 [Visual Basic — konwencje kodowania](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Przegląda wytyczne opracowano próbek w tej dokumentacji.  
  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Opisuje sposób selektywnie kompilacji określonego bloki kodu podczas kierowania kompilatora, aby zignorować innych użytkowników.  
  
 [Porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 Pokazano, jak długo instrukcje do wielu linii podziału i łączenie krótkich instrukcji w jednym wierszu.  
  
 [Porady: zwijanie i ukrywanie fragmentów kodu](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Pokazuje, jak zwijanie i ukrywanie fragmentów kodu w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] edytora kodu.  
  
 [Porady: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Pokazuje, jak zaznacz wiersz kodu, aby zidentyfikować go do użytku w instrukcjach takich jak `On Error Goto`.  
  
 [Znaki specjalne w Code](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Pokazuje, jak i gdzie można używać znaków innych niż alfanumeryczne i inne niż alfanumeryczne.  
  
 [Komentarze w kodzie](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 W tym artykule omówiono sposób dodawania opisową komentarze w kodzie.  
  
 [Słowa kluczowe jako nazwy elementów w Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 W tym artykule opisano sposób użycia nawiasów (`[]`) do rozdzielenia nazwy zmiennych, które są również [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] słów kluczowych.  
  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 W tym artykule opisano różne sposoby odwołań do elementów [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 [Ograniczenia Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 W tym artykule omówiono usunięcie znane ograniczenia kodowania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Związane z typografią i kodami konwencje](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Miejsce na standardowej konwencji kodowania dla [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 [Pisanie kodu](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 W tym artykule opisano funkcje, które ułatwiają zapisu i zarządzać kodem.
