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
ms.openlocfilehash: e4c7704c32c3a6c73e069d0b7129d5386696b438
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402995"
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
 Kończy `#ExternalSource` blok.  
  
## <a name="remarks"></a>Uwagi  

 Ta dyrektywa jest używana tylko przez kompilator i debuger.  
  
 Plik źródłowy może zawierać dyrektywy zewnętrznego źródła, które wskazują mapowanie między określonymi wierszami kodu w pliku źródłowym a tekstem zewnętrznym ze źródłem, takim jak plik. aspx. Jeśli w wyznaczonym kodzie źródłowym wystąpią błędy podczas kompilacji, są one identyfikowane jako pochodzące ze źródła zewnętrznego.  
  
 Dyrektywy źródła zewnętrznego nie mają wpływu na kompilację i nie mogą być zagnieżdżone. Są one przeznaczone do użytku wewnętrznego tylko przez aplikację.  
  
## <a name="see-also"></a>Zobacz też

- [Kompilacja warunkowa](../../programming-guide/program-structure/conditional-compilation.md)
