---
title: Parametry opcjonalne (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e57023f594cfe4cd79d59cc8541fcf18018de0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optional-parameters-visual-basic"></a>Parametry opcjonalne (Visual Basic)
Możesz określić, że parametr procedury jest opcjonalny i nie trzeba do niego przekazywać żadnego argumentu w momencie wywołania procedury. *Parametry opcjonalne* są wskazywane przez `Optional` — słowo kluczowe w definicji procedury. Mają zastosowanie następujące zasady:  
  
-   Każdy parametr opcjonalny w definicji procedury musi określać wartość domyślną.  
  
-   Wartość domyślna dla opcjonalnego parametru musi być wyrażeniem stałym.  
  
-   Każdy parametr występujący w definicji procedury po opcjonalnym parametrze również musi być opcjonalny.  
  
 Deklaracja procedury z opcjonalnym parametrem ma następującą składnię:  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Wywoływanie procedur z opcjonalnymi parametrami  
 Gdy wywołujesz procedurę z opcjonalnym parametrem, możesz wybrać, czy podać argument. Jeśli tego nie zrobisz, procedura użyje wartości domyślnej zadeklarowanej dla tego parametru.  
  
 Jeżeli pomijasz jeden lub więcej argumentów opcjonalnych na liście argumentów, użyj kolejnych średników do oznaczania ich położenia. Następujący przykład wywołania dostarcza pierwszy i czwarty argument, a pomija drugi i trzeci:  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 Poniższy przykład powoduje, że wiele wywołań `MsgBox` funkcji. `MsgBox`ma jeden wymagany parametr i dwa parametry opcjonalne.  
  
 Pierwsze wywołanie w celu `MsgBox` dostarcza wszystkich trzech argumentów w kolejności, która `MsgBox` definiuje je. Drugie wywołanie dostarcza tylko wymagany argument. Wywołania trzecie i czwarte dostarczają argumenty pierwszy i trzeci. Trzecie wywołanie robi to według pozycji, a czwarte wywołanie — według nazwy.  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Określenie, czy opcjonalny argument jest obecny  
 Procedura nie może wykryć w czasie wykonywania, czy podany argument został pominięty lub kod wywołujący ma jawnie przekazywaną wartość domyślną. Jeśli potrzebujesz takiego rozróżnienia, możesz ustawić mało prawdopodobną wartość jako domyślną. Opcjonalny parametr definiuje procedurę `office`, a testy na wartość domyślną `QJZ`, aby zobaczyć, czy ma został pominięty w wywołaniu:  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 Jeśli parametr opcjonalny jest typem referencyjnym, takich jak `String`, można użyć `Nothing` jako wartość domyślną, pod warunkiem nie jest oczekiwana wartość argumentu.  
  
## <a name="optional-parameters-and-overloading"></a>Parametry opcjonalne i przeciążenie  
 Innym sposobem zdefiniowania procedury z opcjonalnymi parametrami jest używanie przeciążenia. Jeśli masz jeden parametr opcjonalny, możesz zdefiniować dwie przeciążone wersje procedury, jedną przyjmującą parametr i jedną bez niego. Takie podejście staje się bardziej skomplikowane w miarę wzrostu liczby parametrów opcjonalnych. Jej zaletą jest jednak, że możesz mieć absolutną pewność, czy program wywołujący dostarcza każdy opcjonalny argument.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md)  
 [Tablice parametrów](./parameter-arrays.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Opcjonalne](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
