---
title: 'Instrukcje: Wstawianie wierszy do bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 8186b90a666a7b75ce626cccb7cc28af38de7c5b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781862"
---
# <a name="how-to-insert-rows-into-the-database"></a>Instrukcje: Wstawianie wierszy do bazy danych

Wiersze są wstawiane do bazy danych przez dodanie obiektów do skojarzonej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekcji, a następnie przesłanie zmian do bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany na odpowiednie polecenia SQL `INSERT` .

> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.

W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [jak: Nawiąż połączenie z](how-to-connect-to-a-database.md)bazą danych.

### <a name="to-insert-a-row-into-the-database"></a>Aby wstawić wiersz do bazy danych

1. Utwórz nowy obiekt, który zawiera dane kolumn do przesłania.

2. Dodaj nowy obiekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekcji skojarzonej z tabelą docelową w bazie danych.

3. Prześlij zmianę do bazy danych.

## <a name="example"></a>Przykład

Poniższy przykład kodu tworzy nowy obiekt typu `Order` i wypełnia go odpowiednimi wartościami. Następnie dodaje nowy obiekt do `Order` kolekcji. Na koniec przesyła zmiany do bazy danych jako nowy wiersz w `Orders` tabeli.

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Metody DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Instrukcje: Przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (Object Relational Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
