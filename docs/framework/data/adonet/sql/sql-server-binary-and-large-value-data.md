---
title: Dane binarne i dużej wartości w programie SQL Server
ms.date: 03/30/2017
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
ms.openlocfilehash: 4d941ad6b7865112b45fd8c20ad89e9236e17b9d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791676"
---
# <a name="sql-server-binary-and-large-value-data"></a>Dane binarne i dużej wartości w programie SQL Server
SQL Server zawiera `max` specyfikator, który rozszerza pojemność magazynu `varchar`dla, `nvarchar`i `varbinary` typów danych. `varchar(max)`, `nvarchar(max)` i`varbinary(max)` są nazywane zbiorczo *typami danych o dużej wartości*. Możesz użyć typów danych o dużej wartości do przechowywania maksymalnie 2 ^ 31-1 bajtów danych.  
  
 SQL Server 2008 wprowadza atrybut FILESTREAM, który nie jest typem danych, ale raczej atrybut, który można zdefiniować w kolumnie, umożliwiając przechowywanie danych dużych wartości w systemie plików, a nie w bazie danych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Modyfikowanie dużej wartości (wartość maksymalna) danych w ADO.NET](modifying-large-value-max-data.md)  
 Opisuje sposób pracy z typami danych o dużej wartości.  
  
 [Dane FILESTREAM](filestream-data.md)  
 Opisuje sposób pracy z danymi o dużej wartości przechowywanych w SQL Server 2008 przy użyciu atrybutu FILESTREAM.  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Operacje danych serwera SQL w ADO.NET](sql-server-data-operations.md)
- [Pobieranie i modyfikowanie danych ADO.NET](../retrieving-and-modifying-data.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
