---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249503"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
Typy wartości i struktury mogą być zadeklarowane nullable.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Jednak nie można użyć nullable deklaracji w połączeniu z wnioskowania o typie. Poniższe przykłady powodują ten błąd.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Identyfikator błędu:** Bc36629  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj `As` klauzuli, aby zadeklarować zmienną jako typ wartości możliwej do wartości null.  
  
## <a name="see-also"></a>Zobacz też

- [Typy o wartości zerowalnej](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
