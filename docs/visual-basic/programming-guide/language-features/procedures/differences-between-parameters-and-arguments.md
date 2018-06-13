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
ms.openlocfilehash: a5075c218371b754ac883b97475ab941811966b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650689"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Różnice pomiędzy parametrami i argumentami (Visual Basic)
W większości przypadków procedury musi mieć niektóre informacje na temat sytuacji, w których została wywołana. Procedury, która wykonuje zadania wielokrotnego lub udostępnionego używa różne informacje dla każdego wywołania. Te informacje składa się z zmienne, stałe i wyrażeń, które przekazujesz do procedury po jej wywołaniu.  
  
 Do przekazywania tych informacji do procedury, definiuje procedurę *parametru*, i przekazuje kod wywołujący *argument* do tego parametru. Można traktować jako odstępu parametr i argument jako samochodów. Tak samo, jak różnych samochodów można zrezygnować w odstępu w różnym czasie, kod wywołujący może przekazać inny argument do tego samego parametru za każdym razem, gdy jego wywołuje procedurę.  
  
## <a name="parameters"></a>Parametry  
 A *parametr* reprezentuje wartość, która procedura oczekuje po jej wywołać. Deklaracja procedury definiuje jego parametrów.  
  
 Podczas definiowania `Function` lub `Sub` procedury, możesz określić *listy parametrów* w nawiasach bezpośrednio po nazwie procedury. Dla każdego parametru należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)). Można również określić, że parametr jest opcjonalny. Oznacza to, że kod wywołujący nie ma przekazać wartość jego.  
  
 Nazwa każdego parametru służy jako *zmiennej lokalnej* w procedurze. Użyj nazwy parametru tak samo jak inne zmiennej.  
  
## <a name="arguments"></a>Argumenty  
 *Argument* reprezentuje wartość, który jest przekazywany do parametru procedury wywołania tej procedury. Kod wywołujący zawiera argumenty, gdy wywołuje procedurę.  
  
 Podczas wywoływania `Function` lub `Sub` procedury obejmują *listy argumentów* w nawiasach bezpośrednio po nazwie procedury. Każdy argument odnosi się do parametru w tej samej pozycji w liście.  
  
 W przeciwieństwie do definicji parametru argumenty nie ma nazwy. Każdy argument jest wyrażenie, które może zawierać zero lub więcej zmiennych, stałe i literały. Typ danych obliczane wyrażenie zwykle powinna być zgodna typu danych zdefiniowanego dla odpowiadającego mu parametru, a w każdym przypadku musi być możliwe do przekonwertowania na typ parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)  
 [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Procedury rekursywne](./recursive-procedures.md)  
 [Przeciążanie procedury](./procedure-overloading.md)
