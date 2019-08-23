---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 2819cd5d2533e8e289735c3df2b39df952968e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938730"
---
# <a name="how-to-update-rows-in-the-database"></a>Instrukcje: Aktualizowanie wierszy w bazie danych
Wiersze w bazie danych można aktualizować, modyfikując wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcją, a następnie przesyłając zmiany do bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany na odpowiednie polecenia SQL `UPDATE` .  
  
> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.  
  
 W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)bazą danych.  
  
### <a name="to-update-a-row-in-the-database"></a>Aby zaktualizować wiersz w bazie danych  
  
1. Wykonaj zapytanie względem bazy danych, aby wiersz został zaktualizowany.  
  
2. Wprowadź żądane zmiany wartości elementów członkowskich w obiekcie wynikiem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
3. Prześlij zmiany do bazy danych programu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje zapytanie do bazy danych w kolejności #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w obiekcie wyniku `Order` . Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych jako zmiany w `ShipName` kolumnach i. `ShipVia`  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
