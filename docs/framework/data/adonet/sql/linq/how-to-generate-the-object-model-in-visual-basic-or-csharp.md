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
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Przewodnik programowania w języku](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [LINQ do SQL modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Learning przez — wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Porady: dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [Mapowanie opartych na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Mapowanie zewnętrznych](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Tworzenie modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
