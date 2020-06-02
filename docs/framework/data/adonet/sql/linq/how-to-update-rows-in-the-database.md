---
title: 'Instrukcje: Aktualizowanie wierszy w bazie danych'
description: Dowiedz się, jak aktualizować wiersze w bazie danych, modyfikując LINQ to SQL obiektów w kolekcji powiązanej z tabelą. LINQ to SQL tłumaczy Dodatki do poleceń aktualizacji SQL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286342"
---
# <a name="how-to-update-rows-in-the-database"></a>Instrukcje: Aktualizowanie wierszy w bazie danych

Wiersze w bazie danych można aktualizować, modyfikując wartości elementów członkowskich obiektów skojarzonych z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcją, a następnie przesyłając zmiany do bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany na odpowiednie `UPDATE` polecenia SQL.

> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody dla `Insert` , `Update` i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.

W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [How to: Connect to a Database](how-to-connect-to-a-database.md).

### <a name="to-update-a-row-in-the-database"></a>Aby zaktualizować wiersz w bazie danych

1. Wykonaj zapytanie względem bazy danych, aby wiersz został zaktualizowany.

2. Wprowadź żądane zmiany wartości elementów członkowskich w obiekcie wynikiem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

3. Prześlij zmiany do bazy danych programu.

## <a name="example"></a>Przykład

Poniższy przykład wykonuje zapytanie do bazy danych w kolejności #11000, a następnie zmienia wartości `ShipName` i `ShipVia` w `Order` obiekcie wyniku. Na koniec zmiany tych wartości elementów członkowskich są przesyłane do bazy danych jako zmiany w `ShipName` `ShipVia` kolumnach i.

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
