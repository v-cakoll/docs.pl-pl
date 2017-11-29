---
title: Struktury decyzji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38820b6ca0a8f716dcaa28644bb25eb4899bd511
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="decision-structures-visual-basic"></a>Struktury decyzji (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Umożliwia warunkach testowych i wykonywać różne operacje, w zależności od wyniki tego testu. Można sprawdzić warunku jest PRAWDA lub FAŁSZ, różnych wartości wyrażenia lub różne wyjątki generowane, gdy wykonanie serię instrukcji.  
  
 Na poniższej ilustracji przedstawiono strukturę decyzji, sprawdza, czy warunek jest spełniony, który wykonuje różne akcje w zależności od tego, czy ma wartość PRAWDA lub FAŁSZ.  
  
 ![Schemat blokowy If... Następnie... Else budowa](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "ifthenelse —")  
Wykonywania różnych akcji, gdy warunek ma wartość PRAWDA, a gdy ma wartość false  
  
## <a name="ifthenelse-construction"></a>IF... Następnie... Else budowa  
 `If...Then...Else`konstrukcje umożliwiają testu dla co najmniej jednego warunku i uruchom jedną lub więcej instrukcji w zależności od każdego warunku. Można przetestować warunków, a następnie podjąć działania w następujący sposób:  
  
-   Uruchom jednego lub więcej instrukcji, gdy jest warunek`True`  
  
-   Uruchom jednego lub więcej instrukcji, gdy jest warunek`False`  
  
-   Uruchamianie niektórych instrukcji, gdy jest warunek `True` oraz innym osobom, jeśli jest`False`  
  
-   Test dodatkowy warunek, w przypadku warunku wstępnego`False`  
  
 Struktura kontroli, która oferuje wszystkie te możliwości to [Jeśli... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Można użyć wersji jeden wiersz, jeśli masz tylko jeden test i jednej instrukcji do uruchomienia. Jeśli masz bardziej złożonego zestawu elementów warunków i akcji, można użyć wersji wielu linii.  
  
## <a name="selectcase-construction"></a>Wybierz... Wielkość konstrukcji  
 `Select...Case` Konstrukcji pozwala obliczyć wyrażenia, jeden raz, a następnie uruchom różne zestawy instrukcji w oparciu o różne możliwe wartości. Aby uzyskać więcej informacji, zobacz [wybierz... Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... CATCH... Na koniec konstrukcji  
 `Try...Catch...Finally`konstrukcje umożliwiają uruchamianie zestaw instrukcji w środowisku, który zachowuje formantu, jeśli dowolny z instrukcji powoduje zgłoszenie wyjątku. Można wykonać różne akcje dla różnych wyjątków. Opcjonalnie można określić blok kodu uruchamianego przed zakończeniem pracy całego `Try...Catch...Finally` konstrukcji, niezależnie od tego, jakie występuje. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Dla wielu struktur kontroli po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze wyróżniono. Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji, wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`, i `End If` są wyróżniane w konstrukcji. Aby przejść do następnej lub poprzedniej wyróżnione słowa kluczowego, naciśnij kombinację klawiszy CTRL + SHIFT + Strzałka w dół strzałkę lub CTRL + SHIFT + Strzałka w górę, strzałki.  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Jeśli — Operator](../../../../visual-basic/language-reference/operators/if-operator.md)
