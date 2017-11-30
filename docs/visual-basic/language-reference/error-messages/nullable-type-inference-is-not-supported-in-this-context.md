---
title: "Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords: BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
Typy wartości i struktury mogą być deklarowane wartości null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Jednak wartości null deklaracji nie można używać w połączeniu z wnioskowanie o typie. Poniższe przykłady być przyczyną tego błędu.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Identyfikator błędu:** BC36629  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj `As` klauzuli, aby zadeklarować zmiennej jako wartości null.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy dopuszczające wartości zerowe wartości](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
