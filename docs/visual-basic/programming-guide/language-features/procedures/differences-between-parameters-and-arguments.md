---
title: Różnice pomiędzy parametrami i argumentami (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: a69b956c7cffcc2a26916d6fc92f23dd4e2322d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864250"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Różnice pomiędzy parametrami i argumentami (Visual Basic)
W większości przypadków procedura musi mieć pewne informacje o sytuacjach, w których została wywołana. Procedura, która wykonuje zadania powtórzonych lub udostępnione używa różne informacje dla każdego wywołania. Ten zawiera zmienne, stałe i wyrażeń, które przekazujesz do procedury, gdy wywołujesz ją.  
  
 Do przekazywania tych informacji do procedury, definiuje procedurę *parametru*, i kod wywołujący przekazuje *argument* do tego parametru. Można traktować jako odstępu parametr i argument jako samochodów. Tak samo, jak różnych samochodów można zrezygnować w odstępu w różnym czasie, kod wywołujący może przekazać innego argumentu do tego samego parametru, za każdym razem, gdy jej wywołuje procedurę.  
  
## <a name="parameters"></a>Parametry  
 A *parametr* reprezentuje wartość, która procedura oczekuje przekazania podczas jego wywoływania. Deklaracja procedury definiuje jego parametrów.  
  
 Podczas definiowania `Function` lub `Sub` procedury, należy określić *listy parametrów* w nawiasach bezpośrednio po Nazwa procedury. Dla każdego parametru, należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Można również określić, że parametr jest opcjonalny. Oznacza to, że kod wywołujący nie ma przekazać wartości.  
  
 Nazwa każdego parametru służy jako *zmienna lokalna* w procedurze. Użyj nazwy parametru tak samo jak inne zmienne.  
  
## <a name="arguments"></a>Argumenty  
 *Argument* reprezentuje wartość, którą przekazać do parametru procedury po wywołaniu procedury. Kod wywołujący dostarcza argumentów, gdy wywołuje procedurę.  
  
 Gdy wywołujesz `Function` lub `Sub` procedury obejmują *listy argumentów* w nawiasach bezpośrednio po Nazwa procedury. Każdy argument odnosi się do parametru w tej samej pozycji na liście.  
  
 W przeciwieństwie do definicji parametru argumentów nie ma nazwy. Każdy argument jest wyrażenia, które może zawierać zero lub więcej zmiennych, stałych i literały. Typ danych obliczane wyrażenie zazwyczaj powinna być zgodna z typem danych zdefiniowanym dla odpowiedniego parametru, a w każdym przypadku musi być konwertowany na typ parametru.  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: Definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Instrukcje: Przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
