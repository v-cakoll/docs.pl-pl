---
title: 'Instrukcje: Wywoływanie funkcji bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: c9cb8d32227447d3808dc250a39fef0867257a77
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250780"
---
# <a name="how-to-call-database-functions"></a>Instrukcje: Wywoływanie funkcji bazy danych
<xref:System.Data.Objects.SqlClient.SqlFunctions> Klasa zawiera metody, które uwidaczniają SQL Server funkcje używane w zapytaniach LINQ to Entities. W przypadku używania <xref:System.Data.Objects.SqlClient.SqlFunctions> metod w LINQ to Entities zapytaniach odpowiednie funkcje bazy danych są wykonywane w bazie danych programu.  
  
> [!NOTE]
> Funkcje bazy danych, które wykonują obliczenia na zestawie wartości i zwracają pojedynczą wartość (znaną również jako zagregowane funkcje bazy danych), mogą być wywoływane bezpośrednio. Inne funkcje kanoniczne można wywołać tylko jako część zapytania LINQ to Entities. Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji. Aby uzyskać więcej informacji, zobacz drugi przykład poniżej.  
  
> [!NOTE]
> Metody w <xref:System.Data.Objects.SqlClient.SqlFunctions> klasie są specyficzne dla SQL Server funkcji. Podobne klasy, które uwidaczniają funkcje bazy danych, mogą być dostępne przez innych dostawców.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Przykład wykonuje kwerendę LINQ to Entities, która używa <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> metody do zwracania wszystkich kontaktów, których nazwisko zaczyna się od "si":  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://archive.codeplex.com/?p=msftdbprodsamples). Przykład wywołuje metodę Aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> bezpośrednio. Należy zauważyć, <xref:System.Data.Objects.ObjectQuery%601> że do funkcji jest przenoszona funkcja, która umożliwia jej wywoływanie bez części zapytania LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
