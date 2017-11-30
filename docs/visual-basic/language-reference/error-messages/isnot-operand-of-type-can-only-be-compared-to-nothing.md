---
title: "&#39; IsNot &#39; Argument typu &#39; typename &#39; można porównywać tylko z &#39; Nie &#39; ponieważ &#39; typename &#39; jest to typ dopuszczający wartość null"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords: BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39; IsNot &#39; Argument typu &#39; typename &#39; można porównywać tylko z &#39; Nie &#39; ponieważ &#39; typename &#39; jest to typ dopuszczający wartość null
Zmienna zadeklarowana jako wartości null ma zostały w porównaniu do wyrażenia innych niż `Nothing` przy użyciu `IsNot` operatora.  
  
 **Identyfikator błędu:** BC32128  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Do innych niż porównania typu dopuszczającego wartości null do wyrażenia `Nothing` za pomocą `IsNot` podmiot, wywołania `GetType` metody na typ dopuszczający wartość null i porównanie wyniku do wyrażenia, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy dopuszczające wartości zerowe wartości](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot — Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
