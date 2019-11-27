---
title: '#ExternalSource, dyrektywa'
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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343833"
---
# <a name="externalsource-directive"></a>#ExternalSource — dyrektywa

Wskazuje mapowanie między określonymi wierszami kodu źródłowego a tekstem zewnętrznym do źródła.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Części  

 `StringLiteral`  
 Ścieżka do zewnętrznego źródła.  
  
 `IntLiteral`  
 Numer wiersza pierwszego wiersza zewnętrznego źródła.  
  
 `LogicalLine`  
 Wiersz, w którym wystąpił błąd w zewnętrznym źródle.  
  
 `#End ExternalSource`  
 Kończy blok `#ExternalSource`.  
  
## <a name="remarks"></a>Uwagi  

 Ta dyrektywa jest używana tylko przez kompilator i debuger.  
  
 Plik źródłowy może zawierać dyrektywy zewnętrznego źródła, które wskazują mapowanie między określonymi wierszami kodu w pliku źródłowym a tekstem zewnętrznym ze źródłem, takim jak plik. aspx. Jeśli w wyznaczonym kodzie źródłowym wystąpią błędy podczas kompilacji, są one identyfikowane jako pochodzące ze źródła zewnętrznego.  
  
 Dyrektywy źródła zewnętrznego nie mają wpływu na kompilację i nie mogą być zagnieżdżone. Są one przeznaczone do użytku wewnętrznego tylko przez aplikację.  
  
## <a name="see-also"></a>Zobacz także

- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
