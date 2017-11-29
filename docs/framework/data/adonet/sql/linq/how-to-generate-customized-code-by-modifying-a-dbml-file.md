---
title: 'Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 743e938df0b9c7f12a9c3a11a4b5558137add529
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML
Możesz wygenerować [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] lub kodu źródłowego C# z pliku metadanych bazy danych markup language (.dbml). Takie podejście umożliwia dostosować domyślny plik .dbml, aby wygenerować kod mapowania aplikacji. Jest to zaawansowana funkcja.  
  
 Kroki tego procesu są następujące:  
  
1.  Wygeneruj plik .dbml.  
  
2.  Edytor do zmodyfikowania pliku: .dbml. Należy pamiętać, że plik .dbml musi sprawdzania poprawności schematu pliku definicji (XSD) dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml plików. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Generowanie [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] lub kodu źródłowego C#.  
  
 Poniższe przykłady użyć narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje plik .dbml z przykładowej bazy danych Northwind. Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwa pliku MDF.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] lub C# pliku kodu źródłowego z pliku .dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Tworzenie modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
