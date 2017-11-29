---
title: "Numeryczne i operatory porównania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a>Numeryczne i operatory porównania
Operatory arytmetyczne i porównanie działać zgodnie z oczekiwaniami w środowisko uruchomieniowe języka wspólnego (CLR) z wyjątkiem w następujący sposób:  
  
-   Na liczby zmiennoprzecinkowe SQL nie obsługuje operator modulo.  
  
-   SQL nie obsługuje arytmetyczne niezaznaczone.  
  
-   Operatory inkrementacji i dekrementacji powodować efekty uboczne, podczas ich używać w wyrażeniach, które nie mogą być replikowane w języku SQL i w związku z tym nie obsługują.  
  
## <a name="supported-operators"></a>Operatory obsługiwane  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje następujące operatory.  
  
-   Operatory arytmetyczne podstawowe:  
  
    -   `+`  
  
    -   `-`(odejmowanie)  
  
    -   `*`  
  
    -   `/`  
  
    -   Dzielenie liczby całkowitej Visual Basic (`\`)  
  
    -   `%`(Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-`(jednoargumentowy negacji)  
  
-   Operatory porównania podstawowe:  
  
    -   Visual Basic `=` i C#`==`  
  
    -   Visual Basic `<>` i C#`!=`  
  
    -   Visual Basic`Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operatory C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operatory](../../../../../visual-basic/language-reference/operators/index.md)
