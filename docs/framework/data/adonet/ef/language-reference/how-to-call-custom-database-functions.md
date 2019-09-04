---
title: 'Instrukcje: Wywoływanie niestandardowych funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: b7f483d8dc7c6d0160ec211140726c9d732f0268
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250808"
---
# <a name="how-to-call-custom-database-functions"></a>Instrukcje: Wywoływanie niestandardowych funkcji bazy danych
W tym temacie opisano sposób wywoływania funkcji niestandardowych, które są zdefiniowane w bazie danych z zapytań LINQ to Entities.  
  
 Funkcje bazy danych, które są wywoływane z zapytań LINQ to Entities są wykonywane w bazie danych programu. Wykonywanie funkcji w bazie danych może zwiększyć wydajność aplikacji.  
  
 Poniższa procedura zawiera konspekt wysokiego poziomu służący do wywoływania niestandardowej funkcji bazy danych. Poniższy przykład zawiera bardziej szczegółowe informacje na temat kroków w procedurze.  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Aby wywołać funkcje niestandardowe zdefiniowane w bazie danych  
  
1. Utwórz funkcję niestandardową w bazie danych.  
  
     Aby uzyskać więcej informacji na temat tworzenia funkcji niestandardowych w SQL Server, zobacz [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).  
  
2. Zadeklaruj funkcję w języku definicji schematu magazynu (SSDL) pliku. edmx. Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowanej w bazie danych.  
  
     Aby uzyskać więcej informacji, zobacz [Funkcja element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).  
  
3. Dodaj odpowiadającą metodę do klasy w kodzie aplikacji i Zastosuj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> do metody należy zauważyć <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> , że parametry i <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> atrybutu są nazwą przestrzeni nazw modelu koncepcyjnego i nazwą funkcji w koncepcyjnej odpowiednio model. Rozpoznawanie nazw funkcji dla LINQ jest rozróżniana wielkość liter.  
  
4. Wywołaj metodę w kwerendzie LINQ to Entities.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak wywołać funkcję niestandardowej bazy danych z poziomu zapytania LINQ to Entities. W przykładzie zastosowano model szkoły. Aby uzyskać informacje o modelu szkoły, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) i [generowanie pliku szkoły. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).  
  
 Poniższy kod dodaje `AvgStudentGrade` funkcję do przykładowej bazy danych szkoły.  
  
> [!NOTE]
> Kroki wywołania niestandardowej bazy danych są takie same, niezależnie od serwera bazy danych. Jednak poniższy kod jest specyficzny dla tworzenia funkcji w bazie danych SQL Server. Kod służący do tworzenia funkcji niestandardowej na innych serwerach bazy danych może się różnić.  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a>Przykład  
 Następnie zadeklaruj funkcję w języku definicji schematu magazynu (SSDL) pliku. edmx. Poniższy kod deklaruje `AvgStudentGrade` funkcję w SSDL:  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a>Przykład  
 Teraz Utwórz metodę i zamapuj ją na funkcję zadeklarowaną w SSDL. Metoda w poniższej klasie jest zamapowana na funkcję zdefiniowaną w SSDL (powyżej) przy użyciu <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>. Gdy ta metoda jest wywoływana, odpowiednia funkcja w bazie danych jest wykonywana.  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Na koniec Wywołaj metodę w kwerendzie LINQ to Entities. Poniższy kod wyświetla nazwisko uczniów i średnią ocenę w konsoli:  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Plik. edmx — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
