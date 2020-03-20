---
title: 'Instrukcje: Wywoływanie niestandardowych funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f3177ab98382506770c4655c62573da5c1d96c69
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848759"
---
# <a name="how-to-call-custom-database-functions"></a>Instrukcje: Wywoływanie niestandardowych funkcji bazy danych

W tym temacie opisano sposób wywoływania funkcji niestandardowych, które są zdefiniowane w bazie danych z w linq do jednostek kwerend.

Funkcje bazy danych, które są wywoływane z LINQ do jednostek kwerendy są wykonywane w bazie danych. Wykonywanie funkcji w bazie danych może poprawić wydajność aplikacji.

Poniższa procedura zawiera konspekt wysokiego poziomu do wywoływania funkcji niestandardowej bazy danych. Poniższy przykład zawiera więcej szczegółów na temat kroków w procedurze.

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a>Aby wywołać funkcje niestandardowe zdefiniowane w bazie danych

1. Utwórz funkcję niestandardową w bazie danych.

     Aby uzyskać więcej informacji na temat tworzenia niestandardowych funkcji w programie SQL Server, zobacz [TWORZENIE FUNKCJI (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).

2. Zadeklaruj funkcję w języku definicji schematu magazynu (SSDL) pliku .edmx. Nazwa funkcji musi być taka sama jak nazwa funkcji zadeklarowanej w bazie danych.

     Aby uzyskać więcej informacji, zobacz [Element funkcji (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).

3. Dodaj odpowiednią metodę do klasy w kodzie <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> aplikacji i zastosuj <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> do metody Należy zauważyć, że parametry i parametry atrybutu są nazwą obszaru nazw modelu koncepcyjnego i nazwą funkcji w modelu koncepcyjnym odpowiednio. Rozpoznawanie nazw funkcji dla LINQ jest rozróżniana wielkość liter.

4. Wywołanie metody w linq do kwerendy jednostek.  

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wywołać funkcję niestandardowej bazy danych z wewnątrz LINQ do kwerendy jednostek. W przykładzie użyto modelu Szkoły. Aby uzyskać informacje o modelu szkoły, zobacz [Tworzenie przykładowej bazy danych szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) i [generowanie pliku edmx szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).

Poniższy kod `AvgStudentGrade` dodaje funkcję do przykładowej bazy danych Szkoły.

> [!NOTE]
> Kroki wywoływania funkcji niestandardowej bazy danych są takie same, niezależnie od serwera bazy danych. Jednak poniższy kod jest specyficzne dla tworzenia funkcji w bazie danych programu SQL Server. Kod do tworzenia funkcji niestandardowej na innych serwerach bazy danych może się różnić.

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a>Przykład

Następnie zadeklaruj funkcję w języku definicji schematu magazynu (SSDL) pliku *.edmx.* Następujący kod deklaruje `AvgStudentGrade` funkcję w SSDL:

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a>Przykład

Teraz utwórz metodę i zamapuj ją na funkcję zadeklarowaną w SSDL. Metoda w następującej klasie jest mapowana na funkcję zdefiniowaną w SSDL (powyżej) za pomocą . <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> Gdy ta metoda jest wywoływana, wykonywana jest odpowiednia funkcja w bazie danych.

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a>Przykład

Na koniec wywołać metodę w LINQ do jednostki kwerendy. W poniższym kodzie są wyświetlane nazwiska uczniów i średnie oceny na konsoli:

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a>Zobacz też

- [Omówienie pliku edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
