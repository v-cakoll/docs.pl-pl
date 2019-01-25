---
title: 'Instrukcje: Bezpośrednie wykonywanie zapytań SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 1caf81df5998e5aaef4ad011a399d70aff43ca9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634461"
---
# <a name="how-to-directly-execute-sql-queries"></a>Instrukcje: Bezpośrednie wykonywanie zapytań SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada zapytania, napisany w sparametryzowane zapytania SQL (w postaci tekstu), a następnie wysyła je do programu SQL server dla przetwarzania.  
  
 SQL nie można wykonać różnych metod, które mogą być dostępne lokalnie na aplikację. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przekonwertować te metody lokalne równoważne operacje i funkcje, które są dostępne w środowisku SQL. Większość metod i operatory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wbudowane typy mają bezpośredni tłumaczenia poleceń SQL. Niektóre można tworzyć z funkcji, które są dostępne. Tymi, które nie wygenerowały generować wyjątki czasu wykonywania. Aby uzyskać więcej informacji, zobacz [mapowanie typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 W przypadkach, gdzie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania jest niewystarczająca dla specjalne zadanie, można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodę, aby wykonać zapytania SQL, a następnie przekonwertować wynik zapytania bezpośrednio do obiektów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przyjęto założenie, że dane dla `Customer` klasy jest rozłożona się powyżej dwóch tabel (serwer customer1 i customer2). Zapytanie zwraca sekwencję `Customer` obiektów.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tak długo, jak nazwy kolumn w wyniki tabelaryczne dopasować kolumny właściwości swojej klasy jednostki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty z dowolnego zapytania SQL.  
  
## <a name="example"></a>Przykład  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda umożliwia również parametry. Użyj następujący kod, aby wykonać zapytanie parametryczne.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametry są wyrażone w tekst zapytania przy użyciu takiej samej notacji nawiasów posługują się `Console.WriteLine()` i `String.Format()`. W rzeczywistości `String.Format()` faktycznie jest wywoływana w ciągu zapytania zostaną podane, zastępując nawiasów parametrów nawiasach z wygenerowanych takich jak nazwy parametrów @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
