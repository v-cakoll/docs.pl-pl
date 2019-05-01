---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: e40866c5160d6850b39133050d09026f5ffd6cc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902944"
---
# <a name="how-to-update-rows-in-the-database"></a>Instrukcje: Aktualizowanie wierszy w bazie danych
Możesz zaktualizować wierszy w bazie danych, zmieniając wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesyłanie zmian do bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zmiany w środowisku SQL odpowiednie `UPDATE` poleceń.  
  
> [!NOTE]
>  Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacje usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Tworzenie procedur składowanych w tym samym celu.  
  
 W następujących krokach założono, że prawidłowy <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Łączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-update-a-row-in-the-database"></a>Aby zaktualizować wiersz w bazie danych  
  
1. Odpytywanie bazy danych dla wiersza do zaktualizowania.  
  
2. Żądane zmiany wartości elementów członkowskich w wynikowym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu.  
  
3. Przesyłanie zmian do bazy danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zapytania bazy danych dla zamówienia #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w wynikowym `Order` obiektu. Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych zgodnie ze zmianami w `ShipName` i `ShipVia` kolumn.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
