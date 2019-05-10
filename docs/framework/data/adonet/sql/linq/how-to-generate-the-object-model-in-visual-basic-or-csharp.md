---
title: 'Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 3feb045ff29527c388e1aa190108f003f96dd4d0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596788"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C\#
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model obiektów w języku programowania jest mapowany w relacyjnej bazie danych. Dwa narzędzia są dostępne dla automatycznego generowania języka Visual Basic lub C# modelu z metadanych istniejącej bazy danych.  
  
- Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do generowania modelu obiektu. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Udostępnia interfejs użytkownika zaawansowanych, które ułatwiają pozyskanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów. Aby uzyskać więcej informacji, zobacz [Linq to SQL Tools w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Narzędzie wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Jeśli nie masz istniejącej bazy danych, aby utworzyć ją z modelu obiektów, można utworzyć modelu obiektu przy użyciu kodu edytora i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Aby uzyskać więcej informacji, zobacz [jak: Dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Dokumentacja [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] zawiera przykłady sposobu generowania języka Visual Basic lub C# modelu obiektów przy użyciu [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Poniższe informacje zawierają przykłady dotyczące używania narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Pokazano w poniższym przykładzie wiersza polecenia SQLMetal tworzy kod języka Visual Basic jako model opartych na atrybutach obiektu w bazie danych Northwind. Procedur przechowywanych i funkcji również są renderowane.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Przykład  
 Pokazano w poniższym przykładzie wiersza polecenia SQLMetal generuje C# kod jako model opartych na atrybutach obiektu w bazie danych Northwind. Procedur przechowywanych i funkcji również są renderowane, a nazwy tabel są automatycznie pluralized.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
