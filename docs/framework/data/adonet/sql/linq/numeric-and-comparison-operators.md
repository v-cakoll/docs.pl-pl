---
title: Operatory numeryczne i porównania
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 9b31fd2d819afbb1e589ad74f23ec139830c68b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212170"
---
# <a name="numeric-and-comparison-operators"></a>Operatory numeryczne i porównania
Operatory arytmetyczne i porównanie działają w oczekiwany sposób w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem sytuacji, w następujący sposób:  
  
-   SQL nie obsługuje operator modulo na liczby zmiennoprzecinkowe.  
  
-   SQL nie obsługuje arytmetyki niezaznaczone.  
  
-   Operatory inkrementacji i dekrementacji spowodować efekty uboczne, gdy będziesz ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym, nie obsługują.  
  
## <a name="supported-operators"></a>Operatory obsługiwane  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje następujące operatory.  
  
-   Podstawowe operatory arytmetyczne:  
  
    -   `+`  
  
    -   `-` (odejmowanie)  
  
    -   `*`  
  
    -   `/`  
  
    -   Dzielenie liczby całkowitej w języku Visual Basic (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (negacja Jednoargumentowa)  
  
-   Operatory porównania podstawowe:  
  
    -   Visual Basic `=` i C# `==`  
  
    -   Visual Basic `<>` i C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operatory języka C#](../../../../../../docs/csharp/language-reference/operators/index.md)
- [Operatory](../../../../../visual-basic/language-reference/operators/index.md)
