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
ms.openlocfilehash: 646d7d217891dc8ea5b78f7ce30fce19fab08316
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977581"
---
# <a name="sub-procedures-visual-basic"></a>Sub — Procedury (Visual Basic)
A `Sub` procedura jest szereg instrukcji ujęta w `Sub` i `End Sub` instrukcji. `Sub` Procedura wykonuje zadanie, a następnie przekazuje sterowanie do kodu wywołującego, ale nie zwraca wartości do wywołującego kodu.  
  
 Każdorazowo, procedura jest wywoływana, jego wykonywane są instrukcje, począwszy od pierwszej instrukcji wykonywalnej po `Sub` instrukcji i kończącą pierwszy `End Sub`, `Exit Sub`, lub `Return` instrukcji napotkany.  
  
 Można zdefiniować `Sub` procedury w modułach, klas i struktur. Domyślnie jest `Public`, oznacza to, należy wywołać go z dowolnego miejsca w aplikacji, które ma dostęp do modułu, klasy lub struktury on zdefiniowany. Termin, *metoda*, w tym artykule opisano `Sub` lub `Function` procedury, która jest dostępne spoza jej Definiowanie modułu, klasy lub struktury. Aby uzyskać więcej informacji, zobacz [procedury](./index.md).  
  
 A `Sub` procedurę można wykonać argumentów, takich jak stałe, zmienne lub wyrażeń, które są przekazywane do niej przez kod wywołujący.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia do deklarowania `Sub` procedura jest następująca:  
  
 `[` *Modyfikatory* `] Sub` *subname* `[(` *listaparametrów* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` Można określić poziom dostępu i informacji o przeładowanie, zastępowanie, udostępnianie i cieniowania. Aby uzyskać więcej informacji, zobacz [Sub — instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklaracja parametru  
 Możesz zadeklarować każdego parametru procedury, podobnie jak sposób Deklarujesz zmienną, określając parametr nazwę i typ danych. Można również określić mechanizm przekazywania i czy parametr jest opcjonalny, lub tablicy parametrów.  
  
 Składnia dla każdego parametru na liście parametrów jest w następujący sposób:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`  *Nazwa parametru*`As`*typu danych*  
  
 Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej w ramach swojej deklaracji. Składnia określająca wartość domyślna jest następująca:  
  
 `Optional [ByVal | ByRef]`  *Nazwa parametru*`As`*datatype*`=`*defaultvalue*  
  
### <a name="parameters-as-local-variables"></a>Parametry jako zmienne lokalne  
 Jeśli kontrola przechodzi do procedury, każdy parametr jest traktowany jako zmienna lokalna. Oznacza to, że jego okres istnienia jest taka sama, jak ta procedura, a jej zakres jest całej procedury.  
  
## <a name="calling-syntax"></a>Składnia wywoływania  
 Wywołuje się `Sub` procedury jawnie za pomocą autonomicznego instrukcji wywołujące. Nie można jej wywołać przy użyciu jego nazwy w wyrażeniu. Należy podać wartości w argumentach, które nie są opcjonalne, a na liście argumentów należy ująć w nawiasy. Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów. Korzystanie z `Call` — słowo kluczowe jest opcjonalne, ale niezalecane.  
  
 Składnia służąca do wywołania `Sub` procedura jest następująca:  
  
 `[Call]`  *subname* `[(` *listaargumentów* `)]`  
  
 Możesz wywołać `Sub` metody z poza klasy, który go definiuje. Najpierw trzeba użyć `New` słowo kluczowe, aby utworzyć wystąpienia klasy lub wywołanie metody zwraca wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md). Następnie można użyć następującej składni wywołać `Sub` metody dla obiektu wystąpienia:  
  
 *Obiekt*. *methodname*`[(`*listaargumentów*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołanie  
 Następujące `Sub` procedura opisuje operator komputera zadań, która aplikacja ma wykonać i wyświetla również sygnaturę czasową. Zamiast duplikowania ten kod na początku każdego zadania, po prostu wywołuje aplikację `tellOperator` z różnych lokalizacji. Każde wywołanie przekazuje ciąg w `task` argument, który identyfikuje zadanie jest uruchamiane.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 W poniższym przykładzie przedstawiono typowe wywołanie `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrukcje: Wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Instrukcje: Wywoływanie programu do obsługi zdarzeń w języku Visual Basic](./how-to-call-an-event-handler.md)
