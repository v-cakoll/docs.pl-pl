---
title: "Porady: wywoływać funkcje w niestandardowej bazie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 181ea834bfc4e252ec57e9dbf76acfb0ea5120fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-custom-database-functions"></a>Porady: wywoływać funkcje w niestandardowej bazie danych
W tym temacie opisano sposób wywołania funkcji niestandardowych, które są zdefiniowane w bazie danych od w składniku LINQ do jednostek zapytań.  
  
 Funkcje bazy danych, które są wywoływane ze składnika LINQ do jednostek zapytań są wykonywane w bazie danych. Wykonywanie funkcji w bazie danych może poprawić wydajność aplikacji.  
  
 Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji w niestandardowej bazie danych. Przykład, w którym następuje zawiera więcej szczegółów na temat czynności opisane w procedurze.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Wywoływanie funkcji niestandardowych, które są zdefiniowane w bazie danych  
  
1.  Tworzenie funkcji niestandardowej w bazie danych.  
  
     Aby uzyskać więcej informacji na temat tworzenia niestandardowych funkcji w programie SQL Server, zobacz [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  Deklarowanie funkcji w magazynie języka definicji schematu (SSDL) pliku edmx. Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowany w bazie danych.  
  
     Aby uzyskać więcej informacji, zobacz [funkcja elementu (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Dodać odpowiedniej metody do klasy w kodzie aplikacji i zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atrybutu jest nazwa przestrzeni nazw modelu koncepcyjnego i nazwa funkcji koncepcyjnego odpowiednio modelu. Funkcja rozpoznawania nazw dla LINQ jest rozróżniana wielkość liter.  
  
4.  Wywołaj metodę w zapytaniu składnika LINQ to Entities.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wywołać funkcję w niestandardowej bazie danych od w LINQ do jednostek zapytania. W przykładzie użyto modelu służbowe. Informacje o modelu służbowe, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx służbowe pliku](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Poniższy kod dodaje `AvgStudentGrade` funkcji do przykładowej bazy danych służbowych.  
  
> [!NOTE]
>  Kroki do wywoływania funkcji w niestandardowej bazie danych są takie same, niezależnie od serwera bazy danych. Poniższy kod jest jednak specyficzne dla tworzenia funkcji w bazie danych programu SQL Server. Kod Tworzenie funkcji niestandardowej w innych serwerów baz danych może się różnić.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Przykład  
 Następnie zadeklarowania funkcji w magazynie języka definicji schematu (SSDL) pliku edmx. Poniższy kod deklaruje `AvgStudentGrade` funkcji w pliku SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Przykład  
 Teraz utworzyć metodę i mapowanie go funkcja zadeklarowany w pliku SSDL. W klasie następujące metody jest zamapowany na funkcję zdefiniowaną w pliku SSDL (powyżej) przy użyciu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Gdy ta metoda jest wywoływana, odpowiednich funkcji w bazie danych jest wykonywana.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Na koniec należy wywołać metodę w zapytaniu składnika LINQ to Entities. Poniższy kod wyświetla nazwisk studentów i średnie klas do konsoli:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie plików edmx](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
