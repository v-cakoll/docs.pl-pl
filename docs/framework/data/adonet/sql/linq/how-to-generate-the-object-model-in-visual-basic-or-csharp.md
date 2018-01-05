---
title: "Porady: Generowanie modelu obiektów w Visual Basic lub C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f4cf0999366a1a677fa729f2d409bea36821eb3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Porady: Generowanie modelu obiektów w Visual Basic lub C# #
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model obiektowy w języku programowania jest mapowany na relacyjnej bazy danych. Dwa narzędzia są dostępne do automatycznego generowania [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] lub modelu C# z istniejącej bazy danych metadanych.  
  
-   Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do wygenerowania modelu typu obiektu. [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] Oferuje interfejs użytkownika zaawansowanych, aby wygenerować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu. Aby uzyskać więcej informacji, zobacz [składnika Linq to SQL narzędzia w programie Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
-   SQLMetal narzędzie wiersza polecenia. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    >  Jeśli nie masz istniejącej bazy danych, aby utworzyć model obiektowy, można utworzyć modelu obiektu przy użyciu kodu edytora i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Aby uzyskać więcej informacji, zobacz [porady: dynamiczne tworzenie bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).  
  
 Dokumentacja [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] przykłady sposób generowania [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] lub model obiektów C# za pomocą [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]. Poniższe informacje zawierają przykłady sposobów użycia narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Tworzy wiersza polecenia SQLMetal pokazano w poniższym przykładzie [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] kodu jako model obiektu na podstawie atrybutów przykładowej bazy danych Northwind. Procedury składowane i funkcje także są renderowane.  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Przykład  
 Wiersz polecenia SQLMetal pokazano w poniższym przykładzie generuje kod w języku C# jako model obiektu na podstawie atrybutów przykładowej bazy danych Northwind. Procedury składowane i funkcje są również wyświetlane, a nazwy tabeli są automatycznie pluralized.  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
