---
title: Error — Typy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: dc7cba394f623ae94a0d9ca8285fc12af8f0dacf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600339"
---
# <a name="error-types-visual-basic"></a>Error — Typy (Visual Basic)
W języku Visual Basic, błędy (nazywane również *wyjątki*) można podzielić na trzy kategorie: błędy składniowe, błędy czasu wykonywania i błędy logiczne.  
  
## <a name="syntax-errors"></a>Błędy składniowe  
 *Błędy składniowe* są te, które pojawiają się podczas pisania kodu. Visual Basic umożliwia sprawdzenie kodu podczas wpisywania w **Edytor kodu** okna i generuje alert w przypadku popełnienia błędu, takie jak błąd pisowni wyrazu lub nieprawidłowo za pomocą elementu języka. Błędy składniowe są najczęściej spotykanym typem błędy. Można je naprawić łatwo w środowisku programowania zaraz po ich wystąpieniu.  
  
> [!NOTE]
>  `Option Explicit` Instrukcja jest jednym ze sposobów uniknięcia błędów składniowych. Wymusza zadeklarować z wyprzedzeniem, wszystkie zmienne, które ma być używany w aplikacji. Dlatego stosowania tych zmiennych w kodzie błędy związane z typografią są przechwytywane natychmiast i można naprawić.  
  
## <a name="run-time-errors"></a>Błędy czasu wykonywania  
 *Błędy środowiska wykonawczego* te, które są wyświetlane tylko po kompilacji i uruchomienia kodu. Obejmują one kod, który może wydawać się być poprawne, ponieważ jej nie ma żadnych błędów składni, ale nie zostanie wykonany. Na przykład może być poprawnie napisać wiersza kodu, aby otworzyć plik. Ale jeśli plik jest uszkodzony, aplikacja nie może przeprowadzić `Open` funkcji i jej przestanie działać. Większość błędów czasu wykonywania można naprawić poprzez ponowne napisanie nieprawidłowy kod, a następnie ponownego kompilowania i ponowne jej uruchomienie.  
  
## <a name="logic-errors"></a>Błędy logiczne  
 *Błędy logiczne* te, które są wyświetlane, gdy aplikacja jest w użyciu. Są one większość często niepożądane i nieoczekiwane wyniki, w odpowiedzi na działania użytkownika. Na przykład, błędnie wpisane klucza lub innych zewnętrznych wpływ może spowodować, że aplikacja przestanie działać w ramach oczekiwanych parametrów lub całkowicie. Błędy logiczne są zwykle najtrudniejsze typu, aby rozwiązać problem, ponieważ nie zawsze jest jasne których pochodzą.  
  
## <a name="see-also"></a>Zobacz także
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Podstawowe informacje o debugerze](/visualstudio/debugger/debugger-basics)
