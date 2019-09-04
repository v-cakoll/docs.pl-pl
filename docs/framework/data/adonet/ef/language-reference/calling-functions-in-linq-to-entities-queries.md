---
title: Wywoływanie funkcji w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251263"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a>Wywoływanie funkcji w zapytaniach składnika LINQ to Entities
W tematach w tej sekcji opisano sposób wywoływania funkcji w LINQ to Entities zapytaniach.  
  
 Klasy <xref:System.Data.Objects.EntityFunctions> i<xref:System.Data.Objects.SqlClient.SqlFunctions> zapewniają dostęp do funkcji kanonicznych i baz danych w ramach Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Wywołaj funkcje](how-to-call-canonical-functions.md) kanoniczne i [instrukcje: Wywołaj funkcje](how-to-call-database-functions.md)bazy danych.  
  
 Proces wywoływania funkcji niestandardowej wymaga wykonania trzech podstawowych czynności:  
  
1. Zdefiniuj funkcję w modelu koncepcyjnym lub Zadeklaruj funkcję w modelu magazynu.  
  
2. Dodaj metodę do aplikacji i zamapuj ją na funkcję w modelu z <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.  
  
3. Wywołaj funkcję w kwerendzie LINQ to Entities.  
  
 Więcej informacji znajduje się w tematach w tej sekcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Wywołaj funkcje kanoniczne](how-to-call-canonical-functions.md)  
  
 [Instrukcje: Wywołania funkcji bazy danych](how-to-call-database-functions.md)  
  
 [Instrukcje: Wywołaj niestandardowe funkcje bazy danych](how-to-call-custom-database-functions.md)  
  
 [Instrukcje: Wywoływanie funkcji zdefiniowanych przez model w zapytaniach](how-to-call-model-defined-functions-in-queries.md)  
  
 [Instrukcje: Wywołaj funkcje zdefiniowane przez model jako metody obiektów](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
- [Funkcje Canonical](canonical-functions.md)
- [Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Instrukcje: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))
