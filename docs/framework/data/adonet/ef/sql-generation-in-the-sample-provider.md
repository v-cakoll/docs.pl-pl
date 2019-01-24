---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: b2397570bb5f312aa6a3955a76234bde508fcc6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505507"
---
# <a name="sql-generation-in-the-sample-provider"></a>Generowanie kodu SQL w dostawcy próbki
[Dostawcy programu Entity Framework przykładowe](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) pokazuje nowe składniki dostawcy danych ADO.NET, który obsługuje [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Z bazą danych programu SQL Server 2005 i lepiej jest implementowany jako otoki dla dostawcy danych System.Data.SqlClient ADO.NET w wersji 2.0.  
  
 Moduł generowanie kodu SQL w dostawcy próbki (znajdujący się w folderze generowanie kodu SQL, z wyjątkiem pliku DmlSqlGenerator.cs) zajmuje DbQueryCommandTree danych wejściowych i tworzy pojedynczą instrukcję SQL SELECT.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Ta sekcja zawiera następujące tematy:  
  
 [Architektura i projekt](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [Przewodnik: Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Zobacz także
- [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
