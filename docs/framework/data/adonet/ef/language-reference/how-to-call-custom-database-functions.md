---
title: 'Porady: wywoływanie niestandardowych funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 4e7c94dce5b50fe93f00aaaa72206be3394faf62
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042286"
---
# <a name="how-to-call-custom-database-functions"></a>Porady: wywoływanie niestandardowych funkcji bazy danych
W tym temacie opisano sposób wywołania funkcji niestandardowych, które są zdefiniowane w bazie danych z w ramach programu LINQ do zapytań jednostki.  
  
 Funkcje bazy danych, które są wywoływane z LINQ do zapytań jednostki są wykonywane w bazie danych. Wykonywanie funkcji w bazie danych może zwiększyć wydajność aplikacji.  
  
 Poniższa procedura zawiera WYSOKOPOZIOMOWY zarys wywoływania funkcji niestandardowej bazy danych. W poniższym przykładzie zapewnia więcej szczegółów na temat czynności opisane w procedurze.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Aby wywołać funkcje niestandardowe, które są zdefiniowane w bazie danych  
  
1.  Tworzenie funkcji niestandardowej w bazie danych.  
  
     Aby uzyskać więcej informacji na temat tworzenia funkcji niestandardowych w programie SQL Server, zobacz [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).  
  
2.  Deklarowanie funkcji w język definicji schematu magazynu (SSDL) pliku edmx. Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowanych w bazie danych.  
  
     Aby uzyskać więcej informacji, zobacz [elementu — funkcja (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).  
  
3.  Dodaj odpowiadającą im metodę do klasy w kodzie aplikacji i zastosować <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody należy pamiętać, że <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atrybutu jest nazwa przestrzeni nazw modelu koncepcyjnego i nazwą funkcji w treści koncepcyjnej model, odpowiednio. Funkcja rozpoznawania nazw dla programu LINQ jest uwzględniana wielkość liter.  
  
4.  Wywołaj metodę w zapytaniu składnika LINQ to Entities.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wywołać funkcję niestandardową bazę danych z w LINQ do kwerendy jednostek. W przykładzie użyto modelu szkoły. Aby uzyskać informacje na temat modelu szkoły, zobacz [tworzenie przykładowej bazy danych School](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) i [generowania edmx School pliku](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).  
  
 Poniższy kod dodaje `AvgStudentGrade` funkcji przykładowej bazy danych School.  
  
> [!NOTE]
>  Kroki do wywoływania funkcji niestandardowej bazy danych są takie same, niezależnie od serwera bazy danych. Jednak kod poniżej dotyczy tworzenia funkcji w bazie danych programu SQL Server. Kod dla tworzenia niestandardowych funkcji na inne serwery baz danych mogą się różnić.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Przykład  
 Następnie można zadeklarować funkcji w język definicji schematu magazynu (SSDL) pliku edmx. Poniższy kod deklaruje `AvgStudentGrade` funkcji w SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Przykład  
 Teraz Utwórz metodę i mapowany do funkcji zadeklarowanych w SSDL. Metoda następujące klasy jest mapowany na funkcję zdefiniowaną w SSDL (powyżej) przy użyciu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Gdy ta metoda jest wywoływana, odpowiednich funkcji w bazie danych jest wykonywana.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Na koniec Wywołaj metodę w zapytaniu składnika LINQ to Entities. Poniższy kod Wyświetla nazwiska uczniów i średni klas do konsoli:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
