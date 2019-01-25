---
title: '#ExternalSource-dyrektywa (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 550934723a5599573be578ce5746ab7520b59dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705972"
---
# <a name="externalsource-directive"></a>#ExternalSource — dyrektywa
Wskazuje mapowanie między poszczególne wiersze kodu źródłowego, a tekstem zewnętrznym do źródła.  
  
## <a name="syntax"></a>Składnia  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Części  
 `StringLiteral`  
 Ścieżka do źródła zewnętrznego.  
  
 `IntLiteral`  
 Numer wiersza w pierwszej linii źródła zewnętrznego.  
  
 `LogicalLine`  
 Wiersz, w którym występuje błąd ze źródła zewnętrznego.  
  
 `#End ExternalSource`  
 Kończy blok `#ExternalSource`.  
  
## <a name="remarks"></a>Uwagi  
 Ta dyrektywa jest używany tylko przez kompilator i debugera.  
  
 Plik źródłowy może zawierać dyrektyw zewnętrznego źródła, które wskazują mapowanie między poszczególne wiersze kodu w pliku źródłowym i tekstem zewnętrznym do źródła, takich jak plik .aspx. Jeśli wystąpią błędy w kodzie źródłowym wyznaczonej podczas kompilacji, są one zidentyfikowane jako pochodzące z zewnętrznego źródła.  
  
 Dyrektywy zewnętrznego źródła, nie mają wpływu na kompilację i nie mogą być zagnieżdżone. Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.  
  
## <a name="see-also"></a>Zobacz także
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
