---
title: Funkcje zdefiniowane przez użytkownika (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 9ddafb18a10ff2313fd27eab453907054a35218a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248771"
---
# <a name="user-defined-functions-entity-sql"></a>Funkcje zdefiniowane przez użytkownika (Entity SQL)
Entity SQL obsługuje wywoływanie funkcji zdefiniowanych przez użytkownika w zapytaniu. Można zdefiniować te funkcje w postaci wbudowanej w zapytaniu [(zobacz How to: Wywoływanie funkcji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))zdefiniowanej przez użytkownika) lub jako części modelu koncepcyjnego (zobacz [How to: Definiowanie funkcji niestandardowych w modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))koncepcyjnym). Funkcje modelu koncepcyjnego są zdefiniowane jako polecenie Entity SQL w elemencie [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) elementu [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) w modelu koncepcyjnym.  
  
 Entity SQL umożliwia zdefiniowanie funkcji w samym poleceniu zapytania. Operator [funkcji](function-entity-sql.md) definiuje funkcje wbudowane. Można zdefiniować wiele funkcji w pojedynczym poleceniu, a funkcje te mogą mieć taką samą nazwę funkcji, o ile sygnatury funkcji są unikatowe. Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążeń funkcji](function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje](functions-entity-sql.md)
