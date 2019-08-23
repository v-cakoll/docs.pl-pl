---
title: 'Instrukcje: Usuwanie wierszy z bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: bae67646d39ad716ed0974987ccbc76e5dd0e58a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940238"
---
# <a name="how-to-delete-rows-from-the-database"></a>Instrukcje: Usuwanie wierszy z bazy danych
Można usunąć wiersze w bazie danych, usuwając odpowiednie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiekty z kolekcji powiązanej z tabelą. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany w odpowiednie polecenia SQL `DELETE` .  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje ani nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz w tabeli zawierającej ograniczenia, musisz wykonać jedno z następujących zadań:  
  
- `ON DELETE CASCADE` Ustaw regułę w ograniczeniu klucza obcego w bazie danych.  
  
- Aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego, użyj własnego kodu.  
  
 W przeciwnym razie jest zgłaszany wyjątek. Zobacz drugi przykład kodu w dalszej części tego tematu.  
  
> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.  
  
 W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bazą danych.  
  
### <a name="to-delete-a-row-in-the-database"></a>Aby usunąć wiersz w bazie danych  
  
1. Wykonaj zapytanie względem bazy danych dla wiersza, który ma zostać usunięty.  
  
2. Wywołaj <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.  
  
3. Prześlij zmianę do bazy danych.  
  
## <a name="example"></a>Przykład  
 Ten pierwszy przykład kodu wysyła zapytanie do bazy danych w celu uzyskania szczegółów zamówienia, które należą do kolejności #11000, oznacza te szczegóły zamówienia do usunięcia i przesyła te zmiany do bazy danych.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W tym drugim przykładzie celem jest usunięcie zamówienia (#10250). Kod najpierw analizuje `OrderDetails` tabelę, aby sprawdzić, czy kolejność usuwania jest tam dostępna. Jeśli zamówienie ma elementy podrzędne, najpierw elementy podrzędne, a następnie zamówienie jest oznaczone do usunięcia. <xref:System.Data.Linq.DataContext> Umieszcza rzeczywiste usuwanie w prawidłowej kolejności, tak aby polecenia Delete wysyłane do bazy danych przestrzegać ograniczeń bazy danych.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
