---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816667"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu. `ParamArray` może służyć tylko na ostatni parametr listę parametrów.  
  
## <a name="remarks"></a>Uwagi  
 `ParamArray` można przekazać dowolną liczbę argumentów do procedury. A `ParamArray` parametr zawsze jest zadeklarowany za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Możesz podać jeden lub więcej argumentów do `ParamArray` , przekazując tablicę odpowiednie dane typu parametru, rozdzielaną przecinkami listę wartości lub nic w ogóle. Aby uzyskać szczegółowe informacje, zobacz "Podczas wywoływania ParamArray" w [Parameter — tablice](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji. Jeśli zdecydujesz się zaakceptować tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmie stosowne działania, jeśli jest zbyt duży dla swojej aplikacji.  
  
 `ParamArray` Modyfikator mogą być używane w tych kontekstach:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
