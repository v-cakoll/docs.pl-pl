---
title: Różnice pomiędzy parametrami i argumentami
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
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403359"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>Różnice pomiędzy parametrami i argumentami (Visual Basic)
W większości przypadków procedura musi mieć pewne informacje dotyczące okoliczności, w których zostało wywołane. Procedura wykonująca powtarzalne lub udostępnione zadania używa różnych informacji dla każdego wywołania. Te informacje składają się ze zmiennych, stałych i wyrażeń, które są przekazywane do procedury po jej wywołaniu.  
  
 Aby przekazać te informacje do procedury, procedura definiuje *parametr*, a wywoływany kod przekazuje *argument* do tego parametru. Można traktować parametr jako miejsce parkingowe i argument jako urządzenie przenośne. Podobnie jak w przypadku różnych samochodów można zaparkować w miejscu parkingowym w różnych godzinach, kod wywołujący może przekazać inny argument do tego samego parametru przy każdym wywołaniu procedury.  
  
## <a name="parameters"></a>Parametry  
 *Parametr* reprezentuje wartość, którą procedura oczekuje na przekazanie po wywołaniu. Deklaracja procedury definiuje jej parametry.  
  
 Podczas definiowania `Function` procedury lub należy `Sub` określić *listę parametrów* w nawiasach bezpośrednio po nazwie procedury. Dla każdego parametru należy określić nazwę, typ danych i mechanizm przekazywania ([ByVal](../../../language-reference/modifiers/byval.md) lub [ByRef](../../../language-reference/modifiers/byref.md)). Możesz również wskazać, że parametr jest opcjonalny. Oznacza to, że wywoływany kod nie musi przekazać do niego wartości.  
  
 Nazwa każdego parametru służy jako *zmienna lokalna* w procedurze. Nazwa parametru jest używana w taki sam sposób, jak w przypadku innych zmiennych.  
  
## <a name="arguments"></a>Argumenty  
 *Argument* reprezentuje wartość przekazana do parametru procedury po wywołaniu procedury. Kod wywołujący dostarcza argumenty, gdy wywołuje procedurę.  
  
 Gdy wywołujesz `Function` procedurę lub, dołączysz `Sub` *listę argumentów* w nawiasach bezpośrednio po nazwie procedury. Każdy argument odpowiada parametrowi w tej samej pozycji na liście.  
  
 W przeciwieństwie do definicji parametrów, argumenty nie mają nazw. Każdy argument jest wyrażeniem, które może zawierać zero lub więcej zmiennych, stałych i literałów. Typ danych obliczanego wyrażenia powinien zwykle być zgodny z typem danych zdefiniowanym dla odpowiedniego parametru, a w każdym przypadku musi być konwertowany na typ parametru.  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Instrukcje: definiowanie parametru dla procedury](./how-to-define-a-parameter-for-a-procedure.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Procedury rekursywne](./recursive-procedures.md)
- [Przeciążanie procedury](./procedure-overloading.md)
