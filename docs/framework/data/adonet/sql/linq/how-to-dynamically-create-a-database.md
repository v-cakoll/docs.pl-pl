---
title: 'Porady: dynamiczne tworzenie bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 122eb705838da00fedd77a01a5d8c4bd3b5f774e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dynamically-create-a-database"></a>Porady: dynamiczne tworzenie bazy danych
W składniku LINQ to SQL model obiektów jest mapowany relacyjnej bazy danych. Mapowanie jest włączane przy użyciu mapowania na podstawie atrybutów lub plik mapowania zewnętrznych do opisania struktury relacyjnej bazy danych. W obu przypadkach ma wystarczającej ilości informacji o relacyjnej bazy danych, możesz utworzyć nowe wystąpienie klasy przy użyciu bazy danych <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Metoda tworzy repliki bazy danych tylko do danych zakodowanych w modelu obiektu. Mapowanie pliki i atrybutów z modelu obiektów może nie Koduj wszystkie informacje o strukturze istniejącej bazy danych. Informacje o mapowaniu nie reprezentuje zawartości funkcje zdefiniowane przez użytkownika, procedury składowane, wyzwalacze lub ograniczenia sprawdzania. To zachowanie jest wystarczająca dla różnych baz danych.  
  
 Można użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody we wszystkich scenariuszach, zwłaszcza, jeśli dostawca znanych danych, takich jak Microsoft SQL Server 2008 jest dostępny. Typowe scenariusze są następujące:  
  
-   Tworzysz aplikację, która automatycznie instaluje się na komputerze klienta.  
  
-   Tworzysz aplikacji klienckiej, która wymaga lokalnej bazy danych można zapisać stanu w trybie offline.  
  
 Można również użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> metody z programem SQL Server przy użyciu pliku .mdf lub nazwę katalogu, w zależności od parametrów połączenia. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa parametrów połączenia, aby zdefiniować bazy danych ma zostać utworzony, a na serwer, który ma być tworzony bazy danych.  
  
> [!NOTE]
>  Jeśli to możliwe, Użyj zintegrowanych zabezpieczeń systemu Windows do łączenia z bazą danych, dzięki czemu hasła nie są wymagane w ciągu połączenia.  
  
## <a name="example"></a>Przykład  
 Następujący kod stanowi przykład tworzenia nowej bazy danych o nazwie MyDVDs.mdf.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Model obiektów służy do tworzenia bazy danych w następujący sposób:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Podczas tworzenia aplikacji, która automatycznie instaluje się na komputerze klienta, zobacz, czy baza danych już istnieje i Porzuć go przed utworzeniem nowego. <xref:System.Data.Linq.DataContext> Klasa udostępnia <xref:System.Data.Linq.DataContext.DatabaseExists%2A> i <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> metod, które zapewniają pomoc podczas tego procesu.  
  
 Poniższy przykład przedstawia sposób którą tych metod można użyć do wdrożenia tego rozwiązania:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
