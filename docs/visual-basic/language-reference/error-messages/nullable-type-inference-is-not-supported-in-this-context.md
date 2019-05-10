---
title: Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 3ab8028062402e33b787a5a8649d93d975918393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665709"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Wnioskowanie typu zerowalnego nie jest obsługiwane w tym kontekście
Typy wartości i struktury można zadeklarować dopuszczającego wartość null.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 Jednak nie można użyć deklaracji dopuszczającego wartość null w połączeniu z wnioskowanie o typie. Poniższe przykłady przyczyny wystąpienia tego błędu.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **Identyfikator błędu:** BC36629  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj `As` klauzulę, aby zadeklarować zmienną jako dopuszczającego wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
