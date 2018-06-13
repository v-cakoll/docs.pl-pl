---
title: Dane binarne i duża wartość serwera SQL
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: c0202f6dc17d36fafb28206e17b71fc6d68d88c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363409"
---
# <a name="sql-server-binary-and-large-value-data"></a>Dane binarne i duża wartość serwera SQL
Program SQL Server stanowi `max` specyfikator, który zwiększa pojemność `varchar`, `nvarchar`, i `varbinary` typy danych. `varchar(max)`, `nvarchar(max)`, i `varbinary(max)` są nazywane *typów danych dużych wartości*. Typy danych dużej wartości umożliwiają przechowywanie maksymalnie 2 ^ 31-1 bajtów danych.  
  
 SQL Server 2008 wprowadza atrybut FILESTREAM, który jest typem danych, ale raczej atrybut, który jest zdefiniowany dla kolumny, dzięki czemu duża wartość danych do przechowywania w systemie plików, zamiast w bazie danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Opisuje sposób pracy z typami danych dużej wartości.  
  
 [Dane FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Opisuje sposób pracy z danymi dużej wartości przechowywane w programie SQL Server 2008 mających atrybut FILESTREAM.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [Operacje danych serwera SQL w ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
