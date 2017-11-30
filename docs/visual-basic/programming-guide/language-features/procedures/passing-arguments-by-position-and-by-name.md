---
title: "Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)
Podczas wywoływania `Sub` lub `Function` procedury, można przekazywać argumenty *według położenia* — w kolejności, w jakiej występują w definicji procedury — lub można przekazać *według nazwy*, bez w odniesieniu do pozycji.  
  
 Jeśli argument według nazw, określ argument deklarowana przez nazwę dwukropek i znak równości (`:=`), a następnie wartość argumentu. Możesz podać Argumenty nazwane w dowolnej kolejności.  
  
 Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Podczas wywoływania tej procedury, można podać argumentów według pozycji, według nazwy lub za pomocą ich kombinacjami.  
  
## <a name="passing-arguments-by-position"></a>Przekazywanie argumentów według pozycji  
 Można wywołać procedury `studentInfo` z jego argumentów przekazywane według pozycji i rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 W przypadku pominięcia opcjonalny argument w postaci listy argument pozycyjny, musi posiadać zamiast niej użyć przecinka. Następujące przykładowe wywołania `studentInfo` bez `age` argumentu:  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Przekazywanie argumentów według nazwy  
 Alternatywnie możesz wywołać `studentInfo` argumentów przekazywane według nazw, również rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Mieszanie argumentów według pozycji i według nazwy  
 Można podać argumenty zarówno według pozycji i według nazwy w wywołaniu procedury pojedynczego, jak pokazano w poniższym przykładzie:  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięcia `age` argumentu, ponieważ `birth` jest przekazywana przez nazwę.  
  
 Jeśli podasz argumenty mieszaniną pozycji i nazwy, argumenty pozycyjne musi występować wszystkie pierwszy. Po podasz argument o nazwie pozostałe argumenty muszą być wszystkie według nazwy.  
  
## <a name="supplying-optional-arguments-by-name"></a>Podanie argumentów opcjonalnych według nazwy  
 Przekazywanie argumentów według nazwy jest szczególnie przydatna podczas wywoływania procedury, która ma więcej niż jeden argument opcjonalny. Należy podać argumenty według nazwy, nie trzeba używać przecinków kolejnych oznaczający brak argumenty pozycyjne. Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumenty, które są przekazywane i które pominięcie.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Ograniczenia dotyczące określenie argumentów według nazwy  
 Nie można przekazywać argumentów przez nazwę, aby uniknąć wprowadzenia wymaganych argumentów. Można pominąć tylko argumenty opcjonalne.  
  
 Tablica parametrów nie można przekazać według nazwy. To dlatego po wywołaniu procedury, podaj nieokreśloną liczbę rozdzielone przecinkami argumenty dla tablicy parametrów, a kompilator nie można skojarzyć więcej niż jeden argument pod jedną nazwą.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Porady: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Parametry opcjonalne](./optional-parameters.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Opcjonalne](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
