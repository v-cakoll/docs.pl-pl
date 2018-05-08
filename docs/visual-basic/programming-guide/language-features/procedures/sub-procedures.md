---
title: Sub — Procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 3286df1a5babfcf7d6b759ff5c9a920bb44f51ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sub-procedures-visual-basic"></a>Sub — Procedury (Visual Basic)
A `Sub` procedura jest serię instrukcji języka Visual Basic otoczony `Sub` i `End Sub` instrukcje. `Sub` Procedury wykonuje zadanie, a następnie zwraca sterowania do kodu wywołującego, ale nie zwraca wartości do wywołującego kodu.  
  
 Każdorazowo po wywołaniu procedury jego instrukcje są wykonywane, zaczynając od pierwszej instrukcji wykonywalnej po `Sub` instrukcji i kończąc pierwszy `End Sub`, `Exit Sub`, lub `Return` Napotkano instrukcję.  
  
 Można zdefiniować `Sub` procedury w modułach, klasy i struktury. Domyślnie jest `Public`, co oznacza, należy go wywoływać z dowolnego miejsca w aplikacji, który ma dostęp do modułu, klasy lub struktury ona zdefiniowana. Termin, *metody*, w tym artykule opisano `Sub` lub `Function` procedury, która jest dostępne spoza jej definiowania modułu, klasy lub struktury. Aby uzyskać więcej informacji, zobacz [procedury](./index.md).  
  
 A `Sub` może potrwać argumenty, takie jak stałe, zmiennych lub wyrażeń, które są przekazywane do niej przez kod wywołujący.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia deklaracji `Sub` procedura wygląda następująco:  
  
 `[` *Modyfikatory* `] Sub` *subname* `[(` *listaparametrów*  `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Można określić poziom dostępu i informacji o przeciążeniu, zastępowanie udostępniania i przesłanianie. Aby uzyskać więcej informacji, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklaracja parametru  
 Należy zadeklarować każdego parametru procedury, podobnie jak jak Zmienna zadeklarowana, określając parametr nazwę i typ danych. Można również określić mechanizm przekazywania i określa, czy parametr jest opcjonalny lub tablicy parametrów.  
  
 Dla każdego parametru na liście parametrów ma następującą składnię:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *Nazwa parametru*`As`*typu danych*   
  
 Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej jako części swojej deklaracji. Składnia służąca do określania wartości domyślnej jest następujący:  
  
 `Optional [ByVal | ByRef]`  *Nazwa parametru*`As`*datatype*`=`*defaultvalue*   
  
### <a name="parameters-as-local-variables"></a>Parametry jako zmienne lokalne  
 Gdy formant przechodzi do procedury, każdy parametr jest traktowany jako zmiennej lokalnej. Oznacza to, że jego okres istnienia jest taka sama, jak te procedury, a jej zakres całej procedury.  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołuje się `Sub` procedury jawnie z autonomicznej instrukcji wywoływania. Nie można wywołać ją przy użyciu nazwy w wyrażeniu. Należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias. Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów. Korzystanie z `Call` — słowo kluczowe jest opcjonalne, ale nie jest zalecane.  
  
 Składnia wywołania `Sub` procedura wygląda następująco:  
  
 `[Call]`  *subname* `[(` *listaargumentów* `)]`  
  
 Możesz wywołać `Sub` metody z poza klasą, który definiuje go. Po pierwsze, należy użyć `New` — słowo kluczowe w celu utworzenia wystąpienia klasy lub wywołanie metody, która zwraca wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md). Następnie można następującej składni wywołań `Sub` metody wystąpienia obiektu:  
  
 *Obiekt*. *methodname*`[(`*listaargumentów*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następujące `Sub` procedury informuje operator komputera zadań, która aplikacja ma wykonać, a także sygnaturę czasową. Zamiast duplikowania ten kod na początku każdego zadania, po prostu wywołuje aplikację `tellOperator` z różnych lokalizacji. Każde wywołanie przekazuje ciąg w `task` argumentu, który identyfikuje zadań jest uruchomiona.  
  
 [!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]  
  
 W poniższym przykładzie przedstawiono typowe wywołania `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Instrukcje: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)  
 [Porady: wywoływanie procedury obsługi zdarzeń w Visual Basic](./how-to-call-an-event-handler.md)
