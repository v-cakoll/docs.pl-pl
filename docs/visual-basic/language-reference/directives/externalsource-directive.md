---
title: '#ExternalSource-dyrektywa'
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586594"
---
# <a name="externalsource-directive"></a>#ExternalSource — dyrektywa
Wskazuje mapowanie między określonych wierszy kodu źródłowego i tekst do źródła zewnętrznego.  
  
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
 Wiersz, w którym występuje błąd z zewnętrznego źródła.  
  
 `#End ExternalSource`  
 Kończy blok `#ExternalSource`.  
  
## <a name="remarks"></a>Uwagi  
 Ta dyrektywa jest używany tylko przez kompilator i debuger.  
  
 Plik źródłowy może zawierać dyrektyw źródła zewnętrznego, wskazujące mapowanie między określonych wierszy kodu w pliku źródłowym i tekst zewnętrznych do źródła, takich jak plik .aspx. Jeśli podczas kompilacji w kodzie źródłowym wyznaczonych zostaną napotkane błędy, są one zidentyfikowane jako pochodzące ze źródła zewnętrznego.  
  
 Dyrektywy źródła zewnętrznego nie mają wpływu na kompilacji i nie mogą być zagnieżdżone. Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
