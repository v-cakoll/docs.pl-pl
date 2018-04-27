---
title: 'Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: dccef2af3d13099b71d3ea8418242e5a5cc16ae5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML
Można wygenerować kodu źródłowego języka Visual Basic lub C# z pliku metadanych bazy danych markup language (.dbml). Takie podejście umożliwia dostosować domyślny plik .dbml, aby wygenerować kod mapowania aplikacji. Jest to zaawansowana funkcja.  
  
 Kroki tego procesu są następujące:  
  
1.  Wygeneruj plik .dbml.  
  
2.  Edytor do zmodyfikowania pliku: .dbml. Należy pamiętać, że plik .dbml musi sprawdzania poprawności schematu pliku definicji (XSD) dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml plików. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Generowanie kodu źródłowego języka Visual Basic lub C#.  
  
 Poniższe przykłady użyć narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje plik .dbml z przykładowej bazy danych Northwind. Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwa pliku MDF.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje Visual Basic lub C# pliku kodu źródłowego z pliku .dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
