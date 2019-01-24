---
title: Binarne i dużej wartości danych programu SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: f6bd62d2e9d2f87947e01b7964c5d151690b62bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643041"
---
# <a name="sql-server-binary-and-large-value-data"></a>Binarne i dużej wartości danych programu SQL Server
SQL Server udostępnia `max` specyfikator, który zwiększa pojemność `varchar`, `nvarchar`, i `varbinary` typów danych. `varchar(max)`, `nvarchar(max)`, i `varbinary(max)` są nazywane *typów danych dużych wartości*. Typy danych dużej wartości można użyć do przechowywania maksymalnie 2 ^ 31-1 bajtów danych.  
  
 Program SQL Server 2008 wprowadzono atrybut FILESTREAM, który jest typem danych, ale raczej atrybut, który może być zdefiniowany dla kolumny, dzięki czemu duża wartość danych mają być przechowywane w systemie plików zamiast w bazie danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 W tym artykule opisano sposób pracy z typami danych duża wartość.  
  
 [Dane FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 W tym artykule opisano sposób pracy z dużą wartość — dane przechowywane w programie SQL Server 2008 mających atrybut FILESTREAM.  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
