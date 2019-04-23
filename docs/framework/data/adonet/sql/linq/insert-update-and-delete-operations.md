---
title: Operacje wstawiania, aktualizowania i usuwania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 6a25ea5fe80da1fed16f44fd3243ebea4d64069f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230683"
---
# <a name="insert-update-and-delete-operations"></a>Operacje wstawiania, aktualizowania i usuwania
Należy wykonać `Insert`, `Update`, i `Delete` operacje w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przez dodawanie, zmienianie i usuwanie obiektów w modelu obiektu. Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy swoje działania do bazy danych SQL i przesyła zmiany do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia maksymalną elastyczność manipulowanie i utrzymanie zmiany wprowadzone do obiektów. Jak najszybciej jednostek dostępnych obiektów (albo pobierając je za pomocą kwerendy lub tworząc je od nowa), możesz zmienić je jako typowe obiekty w aplikacji. Oznacza to możesz zmienić ich wartości, można dodać je do kolekcji i można je usunąć z kolekcji. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Śledzi zmiany i jest gotowa do przesyłania ich w bazie danych, gdy wywołujesz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznają operations usuwanie kaskadowe. Jeśli chcesz usunąć wiersz w tabeli, która ma ograniczenia względem jego, musisz któryś zbiór `ON DELETE CASCADE` reguły ograniczenie klucza obcego w bazie danych lub Użyj własnego kodu, aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego. W przeciwnym razie jest zgłaszany wyjątek. Aby uzyskać więcej informacji, zobacz [jak: Usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Następujące fragmenty użyj `Customer` i `Order` klas z przykładowej bazy danych Northwind. Definicje klas nie są wyświetlane w celu skrócenia programu.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Gdy wywołujesz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatycznie generuje i wykonuje polecenia SQL, które musi mieć do przesłania zmian w bazie danych.  
  
> [!NOTE]
>  To zachowanie można zastąpić za pomocą własnej logiki niestandardowej, zwykle za pomocą procedury składowanej. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzenie procedur składowanych w tym celu.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
