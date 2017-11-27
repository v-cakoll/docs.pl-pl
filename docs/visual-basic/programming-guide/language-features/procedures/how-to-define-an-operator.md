---
title: 'Porady: definiowanie operatora (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a>Porady: definiowanie operatora (Visual Basic)
Jeśli zdefiniowano klasę lub strukturę można zdefiniować zachowanie standardowe — operator (takich jak `*`, `<>`, lub `And`) po co najmniej jeden z argumentów operacji typu klasy lub struktury.  
  
 Zdefiniować operator standardowe procedury operatora w obrębie klasy lub struktury. Wszystkie procedury operatora musi być `Public` `Shared`.  
  
 Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano `+` wywołać operatora dla struktury `height`. Struktura używa mierzony w stopy i cale wysokości. Jeden *CAL* jest 2,54 cm, a drugi *stopka* jest 12 cala. W celu zapewnienia znormalizowane wartości (cali < 12.0), wykonuje konstruktora *modulo* 12 arytmetyczne. `+` Operator używa konstruktora do generowania wartości znormalizowana.  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 Można przetestować struktury `height` następującym kodem.  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury operatorów](./operator-procedures.md)  
 [Porady: Definiowanie operatora konwersji](./how-to-define-a-conversion-operator.md)  
 [Porady: wywoływanie procedury operatora](./how-to-call-an-operator-procedure.md)  
 [Porady: używanie klasy definiującej operatory](./how-to-use-a-class-that-defines-operators.md)  
 [Operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure — instrukcja](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Porady: deklarowanie struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Mod — Operator](../../../../visual-basic/language-reference/operators/mod-operator.md)
