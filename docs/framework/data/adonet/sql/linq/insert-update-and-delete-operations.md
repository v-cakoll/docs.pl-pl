---
title: Wstawiania, aktualizowania i usuwania działań
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 29d87ed22f987a09348cde446d2fd6b11a3c1528
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360507"
---
# <a name="insert-update-and-delete-operations"></a>Wstawiania, aktualizowania i usuwania działań
Należy wykonać `Insert`, `Update`, i `Delete` operacje w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przez dodawanie, zmienianie i usuwanie obiektów w modelu obiektu. Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy akcje użytkownika do bazy danych SQL i przesyła zmiany do bazy danych.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia elastyczność maksymalną manipulowanie i przechowywanie zmiany wprowadzone do obiektów. Jak jednostki dostępnych obiektów (niezależnie, pobierając je za pomocą kwerendy lub tworząc je ponownie), można je zmienić w typowych obiektów w aplikacji. Oznacza to można zmienić ich wartości, należy dodać je do kolekcji i można go usunąć z kolekcji. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Śledzi zmiany i jest gotowy do przesyłania ich do bazy danych podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznaje operacjami usuwania kaskadowego. Jeśli chcesz usunąć wiersza w tabeli, która ma ograniczenia na nim, należy albo zestaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych lub użyj własny kod, aby najpierw usunąć obiekty podrzędne, które zapobiec usunięciu obiektu nadrzędnego. W przeciwnym razie jest zgłaszany wyjątek. Aby uzyskać więcej informacji, zobacz [porady: usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Następujące fragmentów użyj `Customer` i `Order` klasy z przykładowej bazy danych Northwind. Definicje klas nie są wyświetlane do skrócenia.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatycznie generuje i wykonuje polecenia SQL, które muszą mieć do przesłania zmian w bazie danych.  
  
> [!NOTE]
>  Aby zmienić to zachowanie, należy za pomocą własnych niestandardowej logiki, zwykle na procedurę przechowywaną. Aby uzyskać więcej informacji, zobacz [obowiązki deweloperów w zastępowanie domyślne zachowanie](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane w tym celu.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
