---
title: 'Porady: generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 806d0ebc0e9ce970e144d80dbbd4910f9d271e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354575"
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
