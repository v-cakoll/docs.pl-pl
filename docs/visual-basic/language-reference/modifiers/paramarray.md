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
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597363"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu. `ParamArray` może być używany tylko ostatni parametr listy parametrów.  
  
## <a name="remarks"></a>Uwagi  
 `ParamArray` Służy do przekazywania dowolnej liczby argumentów do procedury. A `ParamArray` parametru jest zawsze zadeklarowane za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Możesz podać jeden lub więcej argumentów `ParamArray` przez przekazanie tablicy odpowiednie dane typ parametru, rozdzielana przecinkami lista wartości lub nic w ogóle. Aby uzyskać więcej informacji, zobacz "Podczas wywoływania ParamArray" w [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji. Jeśli akceptujesz tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.  
  
 `ParamArray` Modyfikatora można używać w tych sytuacjach:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
