---
title: 'Instrukcje: generowanie niestandardowego kodu przez zmodyfikowanie pliku DBML'
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: 6619f4b8c0a47b36a0b84fa21bab4109d26ef895
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002942"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a>Instrukcje: generowanie niestandardowego kodu przez zmodyfikowanie pliku DBML
Można generować Visual Basic lub C# kod źródłowy z pliku metadanych języka DBML (Database Markup Language). Takie podejście umożliwia dostosowanie domyślnego pliku DBML przed wygenerowaniem kodu mapowania aplikacji. Jest to funkcja zaawansowana.  
  
 Kroki w tym procesie są następujące:  
  
1. Generuj plik. dbml.  
  
2. Zmodyfikuj plik DBML za pomocą edytora. Należy pamiętać, że plik. dbml musi sprawdzać poprawność pliku definicji schematu (XSD) dla plików [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. dbml. Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](code-generation-in-linq-to-sql.md).  
  
3. Generuj Visual Basic lub C# kod źródłowy.  
  
 W poniższych przykładach użyto narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje plik. dbml z przykładowej bazy danych Northwind. Jako źródło metadanych bazy danych można użyć nazwy bazy danych lub nazwy pliku MDF.  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod generuje Visual Basic lub C# plik kodu źródłowego z pliku. dbml.  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w składniku LINQ to SQL](code-generation-in-linq-to-sql.md)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)
