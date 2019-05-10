---
title: Nieobsługiwana funkcja
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: fb030a5f212be71d99b66f101e5e8411fbe4de33
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618140"
---
# <a name="unsupported-functionality"></a>Nieobsługiwana funkcja
W składniku LINQ to SQL tłumaczenie istniejące środowisko uruchomieniowe języka wspólnego (CLR) nie są dostępne następujące funkcje programu SQL i .NET Framework tworzy:  
  
- `STDDEV`  
  
- `LIKE`  
  
     Mimo że `LIKE` nie jest obsługiwany za pośrednictwem bezpośredniego tłumaczenia podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     LINQ to SQL ma ograniczoną obsługę `DATEDIFF`. Podobne funkcje istnieje w <xref:System.Data.Linq.SqlClient.SqlMethods> klasy.  
  
- `ROUND`  
  
     LINQ to SQL ma ograniczoną obsługę `ROUND`. Aby uzyskać więcej informacji, zobacz [metody System.Math](system-math-methods.md).  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych i funkcje](data-types-and-functions.md)
