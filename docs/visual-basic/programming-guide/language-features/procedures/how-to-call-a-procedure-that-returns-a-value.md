---
title: "Porady: wywoływanie procedury zwracającej wartość (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6d408eed67fa417f42252bb49ecea28d4458382
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a>Porady: wywoływanie procedury zwracającej wartość (Visual Basic)
A `Function` procedury zwraca wartość do wywołującego kodu. Należy wywołać go przez dołączenie jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a>Aby wywołać procedurę Function w wyrażeniu  
  
1.  Użyj `Function` taki sam sposób, należy użyć zmiennej Nazwa procedury. Można użyć `Function` wywoływanie procedury, można użyć zmiennej lub stałą w wyrażeniu dowolnego miejsca.  
  
2.  Po nazwie procedury nawiasami ujmij listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów. Jednak za pomocą nawiasów ułatwia kodu do odczytu.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednich parametrów.  
  
     Alternatywnie można przekazać co najmniej jeden z argumentów według nazwy. Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).  
  
4.  Wartość zwracana z procedury uczestniczy w wyrażeniu podobnie jak wartość zmiennej lub czy stała.  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a>Aby wywołać procedurę Function w instrukcji przypisania  
  
1.  Użyj `Function` nazwę procedury po równości (`=`) Zaloguj się w instrukcji przypisania.  
  
2.  Po nazwie procedury nawiasami ujmij listy argumentów. Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów. Jednak za pomocą nawiasów ułatwia kodu do odczytu.  
  
3.  Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty. Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednie parametry, chyba że przekazaniem ich według nazwy.  
  
4.  Wartość zwracana z procedury są przechowywane w zmiennej lub właściwości po lewej stronie instrukcji przypisania.  
  
## <a name="example"></a>Przykład  
 Następujące przykładowe wywołania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> można pobrać wartości zmiennej środowiskowej systemu operacyjnego. Pierwsze wywołania wiersza `Environ` w wyrażeniu, a drugi wiersz wywołuje ona w instrukcji przypisania. `Environ`pobiera nazwę zmiennej jako jedynego argumentu. Zwraca wartość zmiennej do wywołującego kodu.  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury funkcji](./function-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Porady: Tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Porady: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Porady: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
