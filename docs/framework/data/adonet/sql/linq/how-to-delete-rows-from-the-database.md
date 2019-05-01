---
title: 'Instrukcje: Usuwanie wierszy z bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 401d445e49e3712b8c59fa9bc9a2e53500a5db16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903906"
---
# <a name="how-to-delete-rows-from-the-database"></a>Instrukcje: Usuwanie wierszy z bazy danych
Wierszy w bazie danych można usunąć przez usunięcie odpowiednich [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów z kolekcją związane z tabeli. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zmiany, aby odpowiednie SQL `DELETE` poleceń.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznają operations usuwanie kaskadowe. Aby usunąć wiersz w tabeli, która ma ograniczenia względem go, należy wykonać jedną z następujących zadań:  
  
- Ustaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych.  
  
- Użyj własnego kodu, aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego.  
  
 W przeciwnym razie jest zgłaszany wyjątek. Zobacz drugi przykład kodu w dalszej części tego tematu.  
  
> [!NOTE]
>  Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzenie procedur składowanych w tym samym celu.  
  
 W następujących krokach założono, że prawidłowy <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Łączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Aby usunąć wiersz w bazie danych  
  
1. Odpytywanie bazy danych dla wiersza do usunięcia.  
  
2. Wywołaj <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.  
  
3. Przesyłanie zmian do bazy danych.  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie kod wysyła zapytanie do bazy danych, aby uzyskać szczegóły zamówienia, które należą do 11000 # zamówienia, oznacza tych informacji do usunięcia i przesyła te zmiany w bazie danych.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W drugim przykładzie celem jest usunięcie zamówienie (#10250). Ten kod najpierw sprawdza, czy `OrderDetails` tabelę, aby sprawdzić, czy kolejności do usunięcia ma elementów podrzędnych. Jeśli kolejność ma elementy podrzędne, pierwszy z nich elementy podrzędne, a następnie kolejność są oznaczone do usunięcia. <xref:System.Data.Linq.DataContext> Umieszcza rzeczywista usuwa w odpowiedniej kolejności, tak, aby polecenia delete wysyłane do bazy danych przestrzega ograniczeń bazy danych.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
