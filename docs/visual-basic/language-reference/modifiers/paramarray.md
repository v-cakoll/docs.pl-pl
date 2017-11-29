---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu. `ParamArray`może być używany tylko ostatni parametr listy parametrów.  
  
## <a name="remarks"></a>Uwagi  
 `ParamArray`Służy do przekazywania dowolnej liczby argumentów do procedury. A `ParamArray` parametru jest zawsze zadeklarowane za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Możesz podać jeden lub więcej argumentów `ParamArray` przez przekazanie tablicy odpowiednie dane typ parametru, rozdzielana przecinkami lista wartości lub nic w ogóle. Aby uzyskać więcej informacji, zobacz "Podczas wywoływania ParamArray" w [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji. Jeśli akceptujesz tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.  
  
 `ParamArray` Modyfikatora można używać w tych sytuacjach:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)  
 [Tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
