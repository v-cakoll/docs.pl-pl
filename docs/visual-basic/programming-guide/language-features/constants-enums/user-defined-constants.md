---
title: Stałe zdefiniowane przez użytkownika (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9f4210193aeb386d3a4a76794cc9329cb24b2317
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="user-defined-constants-visual-basic"></a>Stałe zdefiniowane przez użytkownika (Visual Basic)
Stała jest znaczącą nazwę, która ma miejsce, liczby lub ciąg, który nie ulega zmianie. Stałe przechowywać wartości, które, jak nazwa wskazuje, pozostają stałe w trakcie wykonywania aplikacji. Można użyć stałe zdefiniowane przez formanty lub składników, którymi współpracujesz lub Utwórz swój własny. Stałe samodzielnie utworzyć są nazywane *użytkownika*.  
  
 Deklarowanie stałej z `Const` instrukcji, korzystając z tego samego wskazówek, jak do tworzenia nazwy zmiennej. Jeśli `Option Strict` jest `On`, musisz jawnie zadeklarować typu stałej.  
  
## <a name="const-statement-usage"></a>Użycie instrukcji const  
 A `Const` instrukcji można reprezentować matematyczne lub ilość daty/godziny:  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 On również zdefiniować `String` stałe:  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 Wyrażenie po prawej stronie znaku równości ( `=` ) jest często liczba lub ciąg literału, ale również może być wyrażeniem, które powoduje liczbę lub ciąg (chociaż tego wyrażenia nie może zawierać wywołania funkcji). Można nawet Definiowanie stałych pod względem wcześniej zdefiniowanego stałe:  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a>Zakres stałe zdefiniowane przez użytkownika  
 A `Const` instrukcji w zakresie jest taka sama jak zmiennej zadeklarowanej w tej samej lokalizacji. Można określić zakres, w żadnym z następujących sposobów:  
  
-   Aby utworzyć stałą, że istnieje tylko w obrębie procedury, należy zadeklarować w ramach tej procedury.  
  
-   Aby utworzyć stałą dostępne do wszystkich procedur w obrębie klasy, ale nie do kodu poza ten moduł, należy zadeklarować w sekcji deklaracji klasy.  
  
-   Aby utworzyć stałą jest dostępny do wszystkich elementów członkowskich zestawu, ale nie do zewnętrznej klientów zestawu, Zadeklaruj ją przy użyciu `Friend` — słowo kluczowe w sekcji deklaracji klasy.  
  
-   Aby utworzyć stałą dostępne w całej aplikacji, Zadeklaruj ją przy użyciu `Public` — słowo kluczowe w deklaracjach sekcji klasy.  
  
 Aby uzyskać więcej informacji, zobacz [porady: deklarowanie stałej A](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).  
  
### <a name="avoiding-circular-references"></a>Unikanie odwołania cykliczne  
 Ponieważ stałe można zdefiniować pod względem innych stałe, istnieje możliwość tworzenia przypadkowo *cykl*, lub odwołanie cykliczne między co najmniej dwie stałe. Cykl występuje, gdy masz co najmniej dwie stałe publicznych, z których każdy jest określana w kontekście innych, jak w poniższym przykładzie:  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 Jeśli występuje cykl, Visual Basic generuje błąd kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Const, instrukcja](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [Typy danych Stała i Literał](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Stałe i wyliczenia](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Stałe i wyliczenia](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Wyliczenia — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Stałe — przegląd](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Porady: deklarowanie wyliczeń](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Wyliczenia i kwalifikacja nazw](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
