---
title: Generowanie kodu SQL w dostawcy próbki
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248511"
---
# <a name="sql-generation-in-the-sample-provider"></a>Generowanie kodu SQL w dostawcy próbki
[Przykładowy dostawca Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ilustruje nowe składniki dostawców danych ADO.NET, które obsługują [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Działa ona z bazą danych SQL Server 2005 i jest zaimplementowana jako otoka dla Dostawca danych System. Data. SqlClient ADO.NET 2,0.  
  
 Moduł generowania kodu SQL dostawcy przykładowego (znajdującego się w folderze generacji SQL, z wyjątkiem pliku DmlSqlGenerator.cs) przyjmuje wejściowy DbQueryCommandTree i tworzy pojedynczą instrukcję SELECT języka SQL.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Ta sekcja zawiera następujące tematy:  
  
 [Architektura i projekt](architecture-and-design.md)  
  
 [Przewodnik: Generowanie kodu SQL](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kodu SQL](sql-generation.md)
