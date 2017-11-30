---
title: "Sub — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02ba9a999db20abce2106269522c9a3221a00cef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sub-statement-visual-basic"></a>Sub — Instrukcja (Visual Basic)
Deklaruje nazwę, parametry i kod, który definiuje `Sub` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Części  
  
-   `attributelist`  
  
     Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).  
  
-   `Partial`  
  
     Opcjonalny. Wskazuje definicję metody częściowej. Zobacz [metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Opcjonalny. Może to być jedna z następujących czynności:  
  
    -   [Publiczna](../modifiers/public.md)  
  
    -   [Chronione](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Prywatne](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcjonalny. Może to być jedna z następujących czynności:  
  
    -   [Przeciążenia](../modifiers/overloads.md)  
  
    -   [Zastąpienia](../modifiers/overrides.md)  
  
    -   [Możliwym do zastąpienia](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcjonalny. Zobacz [udostępnionych](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).  
  
-   `Async`  
  
     Opcjonalny. Zobacz [Async](../modifiers/async.md).  
  
-   `name`  
  
     Wymagany. Nazwa procedury. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Aby utworzyć procedury konstruktora dla klasy, ustaw nazwę `Sub` procedura `New` — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Opcjonalny. Lista parametrów typu ogólnego procedurę. Zobacz [typu listy](type-list.md).  
  
-   `parameterlist`  
  
     Opcjonalny. Lista nazwy zmiennych lokalnych reprezentujący parametry tej procedury. Zobacz [listy parametrów](parameter-list.md).  
  
-   `Implements`  
  
     Opcjonalny. Wskazuje, że ta procedura implementuje co najmniej jeden `Sub` procedur, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tę procedurę. Zobacz [implementuje instrukcji](implements-statement.md).  
  
-   `implementslist`  
  
     Jeśli wymagane `Implements` podano. Lista `Sub` procedury implementowana.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Każdy `implementedprocedure` ma następujące składni i części:  
  
     `interface.definedname`  
  
    |Część|Opis|  
    |---|---|  
    |`interface`|Wymagany. Nazwa interfejsu implementowanego przez tej procedury zawierający klasy lub struktury.|  
    |`definedname`|Wymagany. Za pomocą którego procedura została określona w nazwie `interface`.|  
  
-   `Handles`  
  
     Opcjonalny. Wskazuje, że ta procedura może obsługiwać jeden lub więcej określonych zdarzeń. Zobacz [obsługuje](handles-clause.md).  
  
-   `eventlist`  
  
     Jeśli wymagane `Handles` podano. Lista zdarzeń, które obsługuje tę procedurę.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Każdy `eventspecifier` ma następujące składni i części:  
  
     `eventvariable.event`  
  
    |Część|Opis|  
    |---|---|  
    |`eventvariable`|Wymagany. Zmienna obiektu zadeklarowane z typem danych klasy lub struktury, który wywołuje zdarzenie.|  
    |`event`|Wymagany. Nazwa zdarzenia, które obsługuje tę procedurę.|  
  
-   `statements`  
  
     Opcjonalny. Blok instrukcji do uruchomienia w ramach tej procedury.  
  
-   `End Sub`  
  
     Kończy definicję tej procedury.  
  
## <a name="remarks"></a>Uwagi  
 Cały kod wykonywalny musi znajdować się w procedurze. Użyj `Sub` procedury, jeśli nie chcesz zwrócić wartość do wywołującego kodu. Użyj `Function` procedury, jeśli chcesz zwrócić wartość.  
  
## <a name="defining-a-sub-procedure"></a>Definiowanie procedury Sub  
 Można zdefiniować `Sub` procedury tylko na poziomie modułu. Kontekst deklaracji procedurę sub dlatego należy klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 `Sub`Domyślnie procedur dostępu publicznego. Modyfikatory dostępu można dostosować ich poziomy dostępu.  
  
 Jeśli procedura używa `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć `Implements` instrukcji poniższą jego `Class` lub `Structure` instrukcji. `Implements` Instrukcja musi zawierać każdy interfejs, który jest określony w `implementslist`. Jednak nazwy za pomocą którego definiuje interfejs `Sub` (w `definedname`) nie musi być zgodna z nazwą w tej procedurze (w `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Zwracanie z procedurę Sub  
 Gdy `Sub` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej po instrukcji, która ją.  
  
 W poniższym przykładzie przedstawiono typ zwracany `Sub` procedury.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 `Exit Sub` i `Return` instrukcje powoduje natychmiastowe wyjście z `Sub` procedury. Dowolną liczbę `Exit Sub` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Sub` i `Return` instrukcje.  
  
## <a name="calling-a-sub-procedure"></a>Wywołanie procedury Sub  
 Należy wywołać `Sub` procedury przy użyciu nazwy procedury w instrukcji i następnie wykonując tej nazwy z listą argumentów w nawiasach. Można pominąć nawiasów, tylko wtedy, gdy nie podawaj żadnych argumentów. Jednak kod jest bardziej przejrzysta zawsze używać nawiasów.  
  
 A `Sub` procedury i `Function` procedura może mieć parametrów i wykonać serię instrukcji. Jednak `Function` procedury zwraca wartość i a `Sub` nie procedury. W związku z tym nie można użyć `Sub` procedury w wyrażeniu.  
  
 Można użyć `Call` — słowo kluczowe podczas wywoływania `Sub` procedura, ale tego słowa kluczowego nie jest zalecane w przypadku zastosowań. Aby uzyskać więcej informacji, zobacz [instrukcji Call](call-statement.md).  
  
 Visual Basic Reorganizuje czasami wyrażenia arytmetyczne, aby zwiększyć wydajność wewnętrznego. Z tego powodu jeśli lista argumentów zawiera wyrażeń, które wywołują inne procedury możesz nie należy założyć, że te wyrażenia zostanie wywołana w określonej kolejności.  
  
## <a name="async-sub-procedures"></a>Async Sub — procedury  
 Korzystając z funkcji asynchronicznych, można wywołać funkcji asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu funkcji lub wyrażenia lambda.  
  
 Jeśli procedura o [Async](../modifiers/async.md) modyfikator, można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w procedurze. Gdy kontrolować osiągnie `Await` wyrażenie w `Async` procedury kontroli zwraca wywołującego i postępu w procedurze jest wstrzymana, aż do zakończenia zadań oczekiwano. Po zakończeniu zadania wykonywania można wznowić w procedurze.  
  
> [!NOTE]
>  `Async` Procedury zwraca do wywołującego po napotkaniu albo pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub na końcu `Async` osiągnięciu procedury cokolwiek nastąpi najpierw.  
  
 Można również zaznaczyć [instrukcji Function](function-statement.md) z `Async` modyfikator. `Async` Funkcja może mieć typ zwracany <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>. Przykład później w tym temacie przedstawiono `Async` funkcja, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>.  
  
 `Async``Sub` procedury są używane przede wszystkim do obsługi zdarzeń, których nie można zwrócić wartość. `Async``Sub` Procedura nie jest oczekiwane oraz funkcji wywołującej `Async``Sub` procedury nie przechwytuje wyjątków który `Sub` zgłasza procedury.  
  
 `Async` Procedury nie można zadeklarować żadnego [ByRef](../modifiers/byref.md) parametrów.  
  
 Aby uzyskać więcej informacji na temat `Async` procedury, zobacz [programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Sub` instrukcji, aby zdefiniować nazwę, parametry i kod, który tworzą treści `Sub` procedury.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `DelayAsync` jest `Async``Function` mający typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync`ma `Return` instrukcji, która zwraca liczbę całkowitą. W związku z tym funkcja deklaracja `DelayAsync` musi mieć typ zwracany `Task(Of Integer)`. Ponieważ typ zwracany jest `Task(Of Integer)`, oceny `Await` wyrażenie w `DoSomethingAsync` tworzy całkowitą, jak przedstawiono na poniższym instrukcji: `Dim result As Integer = Await delayTask`.  
  
 `startButton_Click` Procedura jest przykładem `Async Sub` procedury. Ponieważ `DoSomethingAsync` jest `Async` funkcji, zadanie dla wywołania `DoSomethingAsync` musi być oczekiwane, jak przedstawiono na poniższym instrukcji: `Await DoSomethingAsync()`. `startButton_Click``Sub` Procedury musi być zdefiniowany za pomocą `Async` modyfikator ponieważ ma ona `Await` wyrażenia.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — instrukcja](implements-statement.md)  
 [Function — instrukcja](function-statement.md)  
 [Listy parametrów](parameter-list.md)  
 [Dim — instrukcja](dim-statement.md)  
 [Call — instrukcja](call-statement.md)  
 [Z](of-clause.md)  
 [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Porady: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Procedury rozwiązywania problemów](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Metody częściowe](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
