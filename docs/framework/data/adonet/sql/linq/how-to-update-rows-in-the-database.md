---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: c2055e1dd988352b50a439531ab5533f34a4965e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793136"
---
# <a name="how-to-update-rows-in-the-database"></a>Instrukcje: Aktualizowanie wierszy w bazie danych

Wiersze w bazie danych można aktualizować, modyfikując wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcją, a następnie przesyłając zmiany do bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany na odpowiednie polecenia SQL `UPDATE` .

> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.

W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](how-to-connect-to-a-database.md)bazą danych.

### <a name="to-update-a-row-in-the-database"></a>Aby zaktualizować wiersz w bazie danych

1. Wykonaj zapytanie względem bazy danych, aby wiersz został zaktualizowany.

2. Wprowadź żądane zmiany wartości elementów członkowskich w obiekcie wynikiem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

3. Prześlij zmiany do bazy danych programu.

## <a name="example"></a>Przykład

Poniższy przykład wykonuje zapytanie do bazy danych w kolejności #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w obiekcie wyniku `Order` . Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych jako zmiany w `ShipName` kolumnach i. `ShipVia`

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
