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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
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
 [Operatory języka C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operatory](../../../../../visual-basic/language-reference/operators/index.md)
