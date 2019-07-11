---
title: 'Instrukcje: Usuwanie wierszy z bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 89b552d919898f78c0733c2af4507728f59a3c8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743332"
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
>  Deweloperzy korzystający z programu Visual Studio umożliwia tworzenie procedur składowanych w tym samym celu Object Relational Designer.  
  
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
