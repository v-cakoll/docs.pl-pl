---
title: 'Porady: wstawianie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 4f46e38642d42e3a2e4d5f05e23cc76cf431119b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361737"
---
# <a name="how-to-insert-rows-into-the-database"></a>Porady: wstawianie wierszy w bazie danych
Wstawianie wierszy w bazie danych przez dodawanie obiektów do skojarzonego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesyłanie zmian w bazie danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zmiany odpowiednie SQL `INSERT` poleceń.  
  
> [!NOTE]
>  Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.  
  
 W następujących krokach założono, że jest prawidłowym <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-insert-a-row-into-the-database"></a>Aby wstawić wiersza do bazy danych  
  
1.  Utwórz nowy obiekt, który zawiera kolumny danych do przesłania.  
  
2.  Dodaj nowy obiekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekcji skojarzonych z tabeli docelowej w bazie danych.  
  
3.  Przedstawia zmiany w bazie danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy nowy obiekt typu `Order` i wypełnia odpowiednie wartości. Następnie dodaje nowy obiekt do `Order` kolekcji. Na koniec przesyła zmiany do bazy danych jako nowy wiersz w `Orders` tabeli.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
