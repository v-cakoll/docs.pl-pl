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
ms.openlocfilehash: 8fc5d1afd9e9723e6b3c58e100b0519ef8fdfab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968363"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu. `ParamArray`może być używany tylko dla ostatniego parametru listy parametrów.  
  
## <a name="remarks"></a>Uwagi  
 `ParamArray`umożliwia przekazanie dowolnej liczby argumentów do procedury. Parametr jest zawsze deklarowany przy użyciu [ByVal.](../../../visual-basic/language-reference/modifiers/byval.md) `ParamArray`  
  
 Można podać jeden lub więcej argumentów do `ParamArray` parametru, przekazując tablicę odpowiedniego typu danych, rozdzielaną przecinkami listę wartości lub nic wcale. Aby uzyskać szczegółowe informacje, zobacz "wywoływanie ParamArray" w [tablicach parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
> Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji. Jeśli zaakceptujesz tablicę parametrów z kodu wywołującego, należy przetestować jego długość i wykonać odpowiednie czynności, jeśli jest ono zbyt duże dla aplikacji.  
  
 `ParamArray` Modyfikator może być używany w tych kontekstach:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
