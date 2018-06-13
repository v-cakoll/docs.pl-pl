---
title: 'Porady: tworzenie procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: da4cc299fbe35702990a62b5bf824e3ac71d5902
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649266"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Porady: tworzenie procedury (Visual Basic)
Umieść procedurę między początkową instrukcji deklaracji (`Sub` lub `Function`) i końcowej instrukcji deklaracji (`End Sub` lub `End Function`). Kod wszystkie procedury znajduje się między te instrukcje.  
  
 Procedury nie może zawierać innej procedury, więc jego instrukcje początkowy i końcowy musi znajdować się poza innej procedury.  
  
 Jeśli masz kod, który wykonuje to samo zadanie w różnych miejscach, możesz zapisać zadania raz jako procedura i wywołać go z różnych miejscach w kodzie.  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Aby utworzyć procedury, która nie zwraca wartości  
  
1.  Poza innej procedury należy użyć `Sub` instrukcji, a następnie `End Sub` instrukcji.  
  
2.  W `Sub` instrukcji, wykonaj `Sub` — słowo kluczowe z nazwą procedury ponownie z listą parametrów w nawiasach.  
  
3.  Umieść instrukcji kodu procedury między `Sub` i `End Sub` instrukcje.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedury zwracającej wartość  
  
1.  Poza innej procedury należy użyć `Function` instrukcji, a następnie `End Function` instrukcji.  
  
2.  W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedurą, a następnie z listą parametrów w nawiasy, a następnie `As` klauzuli określający typ danych wartości zwracanej.  
  
3.  Umieść instrukcji kodu procedury między `Function` i `End Function` instrukcje.  
  
4.  Użyj `Return` instrukcji, aby zwrócić wartość do wywołującego kodu.  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Aby połączyć nowe procedury z stare, powtarzających się bloki kodu  
  
1.  Upewnij się, że zdefiniujesz nowe procedury w miejscu, gdzie poprzedni kod ma do niego dostęp.  
  
2.  W bloku kodu stare, powtarzane, Zastąp instrukcji, które wykonują powtarzających się zadań z jednej instrukcji, która wywołuje `Sub` lub `Function` procedury.  
  
3.  Jeśli procedura jest `Function` zwracającego wartość, upewnij się, że instrukcji wywołujący wykonuje akcję z zwracanej wartości, takich jak przechowywanie ich w zmiennej, w przeciwnym razie wartość zostaną utracone.  
  
## <a name="example"></a>Przykład  
 Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a>Zobacz także

 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Procedury rekursywne](./recursive-procedures.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)  
