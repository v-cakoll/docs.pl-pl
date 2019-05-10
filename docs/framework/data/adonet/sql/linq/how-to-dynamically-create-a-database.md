---
title: 'Instrukcje: Dynamiczne tworzenie bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: e5d66b49782d5f26b6d487e655aca6fbd6bdfb1a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623863"
---
# <a name="how-to-dynamically-create-a-database"></a>Instrukcje: Dynamiczne tworzenie bazy danych
W składniku LINQ to SQL na model obiektów jest mapowany w relacyjnej bazie danych. Mapowanie jest włączane przy użyciu opartych na atrybutach mapowania lub pliku mapowania zewnętrznych do opisania struktury relacyjnej bazy danych. W obu przypadkach jest za mało informacji na temat relacyjnej bazy danych, możesz utworzyć nowe wystąpienie bazy danych przy użyciu <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy replikę bazy danych, w jakim informacji zakodowane w modelu obiektów. Mapowanie plików i atrybuty z modelu obiektów może nie kodowania wszystkie informacje o strukturze istniejącej bazy danych. Informacji o mapowaniu nie reprezentują zawartości, funkcje zdefiniowane przez użytkownika, procedury składowane, wyzwalacze lub ograniczenia check. To zachowanie jest wystarczająca dla różnych baz danych.  
  
 Możesz użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody w dowolnej liczbie scenariuszy, zwłaszcza, jeśli dostawca znanych danych, takich jak Microsoft SQL Server 2008 jest dostępny. Typowe scenariusze obejmują następujące czynności:  
  
- Tworzysz aplikację, która automatycznie instaluje się w systemie klienta.  
  
- Tworzysz aplikację kliencką, która wymaga lokalnej bazy danych można zapisać stanu offline.  
  
 Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z programem SQL Server przy użyciu pliku MDF lub nazwę katalogu, w zależności od parametrów połączenia. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa parametrów połączenia Aby zdefiniować utworzenie bazy danych i bazy danych na serwer, który ma zostać utworzony.  
  
> [!NOTE]
>  Możliwe, używaj zintegrowanych zabezpieczeń Windows do łączenia z bazą danych, dzięki czemu hasła nie są wymagane w parametrach połączenia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera przykład sposobu tworzenia nowej bazy danych o nazwie MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Model obiektów umożliwia tworzenie bazy danych, wykonując następujące czynności:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Podczas tworzenia aplikacji, które automatycznie instaluje się w systemie klienta, zobacz, czy baza danych już istnieje i upuść go przed utworzeniem nowej. <xref:System.Data.Linq.DataContext> Klasa udostępnia <xref:System.Data.Linq.DataContext.DatabaseExists%2A> i <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metody ułatwiające przeprowadzenie tego procesu.  
  
 Poniższy przykład przedstawia jeden ze sposobów osiągnięcia tych metod może służyć do wdrożenia tego rozwiązania:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
