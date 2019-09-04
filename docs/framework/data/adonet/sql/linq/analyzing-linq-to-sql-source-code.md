---
title: Analizowanie kodu źródłowego LINQ to SQL
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: dda19800a9aea0d644740c5378f6d5065181993e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248080"
---
# <a name="analyzing-linq-to-sql-source-code"></a>Analizowanie kodu źródłowego LINQ to SQL
Wykonując poniższe kroki, można utworzyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod źródłowy z przykładowej bazy danych Northwind. Można porównać elementy modelu obiektów z elementami bazy danych, aby lepiej zobaczyć, jak są mapowane różne elementy.  
  
> [!NOTE]
> Deweloperzy korzystający z programu Visual Studio mogą używać projektanta O/R do tworzenia tego kodu.  
  
1. Jeśli nie masz jeszcze przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać bezpłatnie. Aby uzyskać więcej informacji, zobacz [Pobieranie przykładowych baz danych](downloading-sample-databases.md).  
  
2. Użyj narzędzia wiersza polecenia SqlMetal, aby wygenerować Visual Basic lub C# plik źródłowy. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Wpisując następujące polecenia w wierszu polecenia, można generować Visual Basic i C# pliki źródłowe, które zawierają procedury składowane i funkcje:  
  
    - `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    - `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](reference.md)
- [Informacje uzupełniające](background-information.md)
