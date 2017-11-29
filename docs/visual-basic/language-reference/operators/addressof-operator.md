---
title: "AddressOf — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a>AddressOf — Operator (Visual Basic)
Tworzy wystąpienia delegata procedury, która odwołuje się do określonej procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>Części  
 `procedurename`  
 Wymagany. Określa procedurę, aby odwoływać się procedury nowo utworzonego obiektu delegowanego.  
  
## <a name="remarks"></a>Uwagi  
 `AddressOf` Operator tworzy delegata funkcji, które wskazuje funkcji określonej przez `procedurename`. Gdy określonej procedury jest metodą wystąpienia następnie delegata funkcji odwołuje się do wystąpienia i metody. Następnie gdy jest wywoływany delegat funkcji określonej metody określone wystąpienie jest wywoływana.  
  
 `AddressOf` Operator może być używany jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można ustalić typu obiektu delegowanego przez kompilator.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć pełnomocnika, aby obsłużyć `Click` zdarzeń przycisku.  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcja uruchomienia wątku.  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Obiekty delegowane](../../../visual-basic/programming-guide/language-features/delegates/index.md)
