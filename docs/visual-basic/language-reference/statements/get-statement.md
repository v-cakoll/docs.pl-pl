---
title: "Get — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1ff062a5e3bf41794bd5b4c90f1e188d6d97480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="get-statement"></a>Get — Instrukcja
Deklaruje `Get` procedury właściwości używane do pobierania wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalnie na maksymalnie jeden `Get` i `Set` instrukcje w tej właściwości. Może to być jedna z następujących czynności:<br /><br /> -   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Opcjonalny. Co najmniej jeden instrukcji, które podczas uruchamiania `Get` właściwości procedura jest wywoływana.|  
|`End Get`|Wymagany. Kończy definicję `Get` procedury właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Dla każdej właściwości musi mieć `Get` procedury właściwości, chyba że właściwość jest oznaczona jako `WriteOnly`. `Get` Procedura służy do zwracania bieżącej wartości właściwości.  
  
 Visual Basic automatycznie wywołuje właściwość `Get` procedury, gdy wartość właściwości zażąda wyrażenia.  
  
 Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji. Nie można zapisać żadnych innych niż te procedury. W szczególności go nie można zapisać bieżącą wartość właściwości. Ta wartość poza właściwości, muszą być przechowywane, ponieważ Jeśli przechowujesz wewnątrz jednej z właściwości procedur procedurę właściwości nie można do niego dostęp. Jest zwykle podejście do przechowywania wartości [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarować zmiennej na tym samym poziomie jako wartość właściwości. Należy zdefiniować `Get` procedurę wewnątrz właściwości, której dotyczy.  
  
 `Get` Procedury Domyślnie poziom dostępu do jego właściwości zawierającego tylko w przypadku `accessmodifier` w `Get` instrukcji.  
  
## <a name="rules"></a>Reguły  
  
-   **Mieszanymi poziomami dostępu.** Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba. Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości. Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Get` procedury `Private`, ale nie `Public`.  
  
     Jeśli definiujesz `ReadOnly` właściwość `Get` procedury reprezentuje cały właściwość. Nie można zadeklarować poziom dostępu różnych `Get`, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.  
  
-   **Typ zwracany.** [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) można zadeklarować typu danych zwracanych wartości. `Get` Procedury automatycznie zwraca typ danych. Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.  
  
     Jeśli `Property` instrukcji nie określa `returntype`, zwraca procedury `Object`.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Zwracanie z procedury.** Gdy `Get` procedura zwraca do kodu wywołującego, wykonanie jest kontynuowane w instrukcji, która żądanej wartości właściwości.  
  
     `Get`procedury własności może zwracać wartości przy użyciu [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) lub wartości zwracanej nazwę właściwości. Aby uzyskać więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     `Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości. Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.  
  
-   **Wartość zwracana.** Zwraca wartość z `Get` procedury, można przypisać wartości do nazwy właściwości lub dołączyć go w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md). `Return` Instrukcja jednocześnie przypisuje `Get` procedura zwraca wartość i kończy procedurę.  
  
     Jeśli używasz `Exit Property` bez przypisywanie wartości do nazwy właściwości `Get` procedury zwraca wartość domyślna dla typu danych właściwości. Aby uzyskać więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Poniższy przykład przedstawia dwa sposoby właściwości tylko do odczytu `quoteForTheDay` może zwrócić wartość przechowywana w zmiennej prywatnej `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Get` instrukcji, aby zwrócić wartość właściwości.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Set — instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit — instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Wskazówki: Definiowanie klas](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
