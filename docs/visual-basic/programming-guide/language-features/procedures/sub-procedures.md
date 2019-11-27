---
title: Sub — Procedury
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
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352525"
---
# <a name="sub-procedures-visual-basic"></a>Sub — Procedury (Visual Basic)
Procedura `Sub` jest serią Visual Basic instrukcji ujętych w instrukcji `Sub` i `End Sub`. Procedura `Sub` wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego, ale nie zwraca wartości do kodu wywołującego.  
  
 Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są wykonywane, rozpoczynając od pierwszej instrukcji wykonywalnej po instrukcji `Sub` i kończąc na pierwszej instrukcji `End Sub`, `Exit Sub`lub `Return`.  
  
 Można zdefiniować `Sub` procedury w modułach, klasach i strukturach. Domyślnie jest `Public`, co oznacza, że można wywołać ją z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany. Termin, *Metoda*, opisuje procedurę `Sub` lub `Function`, do której uzyskano dostęp spoza zdefiniowanego modułu, klasy lub struktury. Aby uzyskać więcej informacji, zobacz [procedur](./index.md).  
  
 Procedura `Sub` może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są przekazane do niego przez wywołujący kod.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Składnia do deklarowania procedury `Sub` jest następująca:  
  
 `[` *modyfikatory* `] Sub`*SubName* `[(` *listaparametrów* `)]`  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 `modifiers` można określić poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania. Aby uzyskać więcej informacji, zobacz [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="parameter-declaration"></a>Deklaracja parametru  
 Każdy parametr procedury deklaruje się podobnie jak w przypadku deklarowania zmiennej, określając nazwę parametru i typ danych. Można również określić mechanizm przekazywania oraz określać, czy parametr jest opcjonalny, czy też tablicą parametrów.  
  
 Składnia każdego parametru na liście parametrów jest następująca:  
  
 `[Optional] [ByVal | ByRef] [ParamArray]`*parametername*`As`*DataType*  
  
 Jeśli parametr jest opcjonalny, należy również podać wartość domyślną w ramach swojej deklaracji. Składnia określająca wartość domyślną jest następująca:  
  
 `Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*  
  
### <a name="parameters-as-local-variables"></a>Parametry jako zmienne lokalne  
 Gdy kontrola przechodzi do procedury, każdy parametr jest traktowany jako zmienna lokalna. Oznacza to, że jego okres istnienia jest taki sam jak w przypadku tej procedury, a jego zakres jest całą procedurą.  
  
## <a name="calling-syntax"></a>Składnia wywołania  
 Procedurę `Sub` należy wywoływać jawnie przy użyciu autonomicznej instrukcji wywołującej. Nie można wywołać go przy użyciu jego nazwy w wyrażeniu. Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach. Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy. Użycie słowa kluczowego `Call` jest opcjonalne, ale nie jest zalecane.  
  
 Składnia wywołania procedury `Sub` jest następująca:  
  
 `[Call]`*SubName* `[(` *listaargumentów* `)]`  
  
 Metodę `Sub` można wywołać spoza klasy, która go definiuje. Najpierw należy użyć słowa kluczowego `New`, aby utworzyć wystąpienie klasy, lub wywołać metodę zwracającą wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md). Następnie można użyć następującej składni, aby wywołać metodę `Sub` w obiekcie wystąpienia:  
  
 *Obiekt*. *methodname*`[(`*listaargumentów*`)]`  
  
### <a name="illustration-of-declaration-and-call"></a>Ilustracja deklaracji i wywołania  
 Poniższa procedura `Sub` informuje operatora komputera, który zadanie ma wykonać aplikacja, a także wyświetla sygnaturę czasową. Zamiast duplikować ten kod na początku każdego zadania, aplikacja właśnie wywołuje `tellOperator` z różnych lokalizacji. Każde wywołanie przekazuje ciąg w argumencie `task`, który identyfikuje uruchomione zadanie.  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 Poniższy przykład przedstawia typowe wywołanie do `tellOperator`.  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Instrukcje: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Instrukcje: wywoływanie procedury obsługi zdarzeń w Visual Basic](./how-to-call-an-event-handler.md)
