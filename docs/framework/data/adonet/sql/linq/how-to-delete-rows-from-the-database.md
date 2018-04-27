---
title: 'Porady: usuwanie wierszy z bazy danych'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: f84531be8bc8ae57db895959513fdc7dd4a8d154
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-delete-rows-from-the-database"></a>Porady: usuwanie wierszy z bazy danych
Można usunąć wierszy w bazie danych przez usunięcie odpowiadającego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektów z kolekcji ich związanych z tabeli. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zmiany, aby odpowiednie SQL `DELETE` poleceń.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje ani nie rozpoznaje operacjami usuwania kaskadowego. Jeśli chcesz usunąć wiersza w tabeli, która ma ograniczenia na nim, należy wykonać jedną z następujących zadań:  
  
-   Ustaw `ON DELETE CASCADE` reguły w ograniczenie klucza obcego w bazie danych.  
  
-   Najpierw usuń obiekty podrzędne, które zapobiec usunięciu obiektu nadrzędnego przy użyciu własnego kodu.  
  
 W przeciwnym razie jest zgłaszany wyjątek. Zobacz drugi przykład kodu w dalszej części tego tematu.  
  
> [!NOTE]
>  Można zastąpić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`, `Update`, i `Delete` bazy danych operacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie Insert, Update i operacji usunięcia](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Za pomocą programu Visual Studio deweloperzy mogą używać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] aby opracować procedury składowane do takiej obsługi.  
  
 W następujących krokach założono, że jest prawidłowym <xref:System.Data.Linq.DataContext> połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [porady: połączenie z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Aby usunąć wiersz w bazie danych  
  
1.  Wyślij zapytanie do bazy danych dla wiersza, który ma zostać usunięty.  
  
2.  Wywołanie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metody.  
  
3.  Przedstawia zmiany w bazie danych.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pierwsze kodu wysyła zapytanie do bazy danych dla szczegółów zamówienia, które należą do 11000 # kolejności, oznacza tych informacji do usunięcia i przesyła te zmiany w bazie danych.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Przykład  
 W drugim przykładzie celem jest usunięcie zamówienia (#10250). Kod najpierw sprawdza, czy `OrderDetails` tabeli, aby sprawdzić, czy kolejność, która ma zostać usunięta ma elementów podrzędnych. Jeśli kolejność ma elementy podrzędne, pierwszy z nich elementów podrzędnych, a następnie kolejność są oznaczone do usunięcia. <xref:System.Data.Linq.DataContext> Umieszcza rzeczywiste usuwa w odpowiedniej kolejności, aby polecenia usuwania wysłanych do bazy danych przestrzegania ograniczeń bazy danych.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
