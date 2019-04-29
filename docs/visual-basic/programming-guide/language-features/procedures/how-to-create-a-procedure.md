---
title: 'Instrukcje: Tworzenie procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 56099d334a03e85b816cf48983cbbead0784ef5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665809"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Instrukcje: Tworzenie procedury (Visual Basic)
Ujmij procedury między początkową instrukcji deklaracji (`Sub` lub `Function`) i końcowej instrukcji deklaracji (`End Sub` lub `End Function`). Kod wszystkie procedury musi się mieścić tych instrukcji.  
  
 Procedury nie może zawierać innej procedury, dzięki czemu jej instrukcji początkowy i końcowy musi znajdować się poza inne procedury.  
  
 Jeśli masz kod, który wykonuje tego samego zadania w różnych miejscach, możesz zapisać zadanie raz jako procedura i wywołać go z różnych miejsc w kodzie.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości  
  
1. Poza innej procedury, należy użyć `Sub` instrukcji, następuje `End Sub` instrukcji.  
  
2. W `Sub` instrukcji, postępuj zgodnie z `Sub` — słowo kluczowe o nazwie procedury, a następnie lista parametrów w nawiasach.  
  
3. Umieść instrukcje kod procedury między `Sub` i `End Sub` instrukcji.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości  
  
1. Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.  
  
2. W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury, a następnie lista parametrów w nawiasach, a następnie `As` klauzuli określający typ danych wartości zwracanej.  
  
3. Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.  
  
4. Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Nawiązywanie połączeń z nową procedurę z stare, powtarzających się bloki kodu  
  
1. Upewnij się, że należy zdefiniować nową procedurę w miejscu, w której stary kod ma do niego dostęp.  
  
2. W bloku kodu stary i powtarzalnych, Zastąp instrukcji, które wykonują powtarzających się zadań przy użyciu pojedynczej instrukcji, która wywołuje `Sub` lub `Function` procedury.  
  
3. Jeśli procedura jest `Function` zwracającego wartość, upewnij się, że instrukcji wywołujący wykonuje akcję z wartością zwróconą, takich jak przechowywanie ich w zmiennej, w przeciwnym razie wartość zostaną utracone.  
  
## <a name="example"></a>Przykład  
 Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
