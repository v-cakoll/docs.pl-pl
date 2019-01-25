---
title: 'Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: b17743f20cf9fcb01cdd39dc7afc3f6b4419ebff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499096"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML
Można wygenerować kodu języka Visual Basic lub C# źródła kodu z pliku metadanych bazy danych markup language (dbml). To podejście oferuje możliwość dostosowywania domyślnego pliku dbml przed wygenerowaniem kodu mapowania aplikacji. Jest to zaawansowana funkcja.  
  
 Kroki w ramach tego procesu są następujące:  
  
1.  Generuje plik dbml.  
  
2.  Użyj edytora do modyfikowania pliku dbml. Należy zauważyć, że plik dbml musi przeprowadzić walidacji względem pliku (XSD) definicji schematu dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dbml, pliki. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).  
  
3.  Generowanie języka Visual Basic lub C# kodu źródłowego.  
  
 W poniższych przykładach używane jest narzędzie wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje plik dbml z przykładowej bazy danych Northwind. Jako źródło dla metadanych bazy danych można użyć nazwy bazy danych lub nazwę pliku MDF.  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje języka Visual Basic lub C# pliku kodu źródłowego, na podstawie pliku dbml.  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Zobacz także
- [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
