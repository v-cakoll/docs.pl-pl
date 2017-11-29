---
title: '#<a name="externalsource-directive"></a>ExternalSource-dyrektywa'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 Kończy `#ExternalSource` bloku.  
  
## <a name="remarks"></a>Uwagi  
 Ta dyrektywa jest używany tylko przez kompilator i debuger.  
  
 Plik źródłowy może zawierać dyrektyw źródła zewnętrznego, wskazujące mapowanie między określonych wierszy kodu w pliku źródłowym i tekst zewnętrznych do źródła, takich jak plik .aspx. Jeśli podczas kompilacji w kodzie źródłowym wyznaczonych zostaną napotkane błędy, są one zidentyfikowane jako pochodzące ze źródła zewnętrznego.  
  
 Dyrektywy źródła zewnętrznego nie mają wpływu na kompilacji i nie mogą być zagnieżdżone. Są one przeznaczone do użytku wewnętrznego przez aplikację tylko.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
