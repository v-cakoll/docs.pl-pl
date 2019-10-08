---
title: 'Instrukcje: Generowanie modelu obiektu w Visual Basic lubC#'
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: 7d2c0600534c93f5884eec48a4bdaa3ce99945e9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002802"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a>Instrukcje: Generowanie modelu obiektów w Visual Basic lub C @ no__t-0
W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] model obiektów w własnym języku programowania jest mapowany na relacyjną bazę danych. Dostępne są dwa narzędzia do automatycznego generowania Visual Basic lub C# modelu z metadanych istniejącej bazy danych.  
  
- W przypadku korzystania z programu Visual Studio można wygenerować model obiektów przy użyciu Object Relational Designer. Projektant O/R udostępnia rozbudowany interfejs użytkownika, który pomaga generować model obiektów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aby uzyskać więcej informacji, zobacz [Narzędzia LINQ to SQL w programie Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).
  
- Narzędzie wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
    > [!NOTE]
    > Jeśli nie masz istniejącej bazy danych i chcesz utworzyć ją na podstawie modelu obiektów, możesz utworzyć model obiektu za pomocą edytora kodu i <xref:System.Data.Linq.DataContext.CreateDatabase%2A>. Aby uzyskać więcej informacji, zobacz [jak: dynamiczne tworzenie bazy danych](how-to-dynamically-create-a-database.md).  
  
 Dokumentacja projektanta O/R zawiera przykłady sposobu generowania Visual Basic lub C# modelu obiektów przy użyciu projektanta o/r. Poniższe informacje zawierają przykłady użycia narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="example"></a>Przykład  
 Wiersz polecenia SQLMetal przedstawiony w poniższym przykładzie generuje kod Visual Basic jako model obiektów opartych na atrybutach przykładowej bazy danych Northwind. Procedury składowane i funkcje są również renderowane.  
  
```console  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a>Przykład  
 Wiersz polecenia SQLMetal przedstawiony w poniższym przykładzie generuje C# kod jako model obiektu oparty na atrybutach przykładowej bazy danych Northwind. Procedury składowane i funkcje są również renderowane, a nazwy tabel są automatycznie umieszczane w liczbie.  
  
```console  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Nauka przez przewodniki](learning-by-walkthroughs.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [Mapowanie oparte na atrybutach](attribute-based-mapping.md)
- [SqlMetal.exe (narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Mapowanie zewnętrzne](external-mapping.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Tworzenie modelu obiektu](creating-the-object-model.md)
