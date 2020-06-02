---
title: 'Instrukcje: Usuwanie wierszy z bazy danych'
description: Informacje o usuwaniu wierszy w bazie danych przez usunięcie LINQ to SQL obiektów z kolekcji powiązanej z tabelą. LINQ to SQL tłumaczy operacje usuwania na polecenia DELETE języka SQL.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286394"
---
# <a name="how-to-delete-rows-from-the-database"></a>Instrukcje: Usuwanie wierszy z bazy danych

Można usunąć wiersze w bazie danych, usuwając odpowiednie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiekty z kolekcji powiązanej z tabelą. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zmiany w odpowiednie `DELETE` polecenia SQL.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje ani nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz w tabeli zawierającej ograniczenia, musisz wykonać jedno z następujących zadań:

- Ustaw `ON DELETE CASCADE` regułę w ograniczeniu klucza obcego w bazie danych.

- Aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego, użyj własnego kodu.

 W przeciwnym razie jest zgłaszany wyjątek. Zobacz drugi przykład kodu w dalszej części tego tematu.

> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody dla `Insert` , `Update` i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.

W poniższych krokach przyjęto założenie, że prawidłowy <xref:System.Data.Linq.DataContext> nawiąże połączenie z bazą danych Northwind. Aby uzyskać więcej informacji, zobacz [How to: Connect to a Database](how-to-connect-to-a-database.md).

### <a name="to-delete-a-row-in-the-database"></a>Aby usunąć wiersz w bazie danych

1. Wykonaj zapytanie względem bazy danych dla wiersza, który ma zostać usunięty.

2. Wywołaj <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metodę.

3. Prześlij zmianę do bazy danych.

## <a name="example"></a>Przykład

Ten pierwszy przykład kodu wysyła zapytanie do bazy danych w celu uzyskania szczegółów zamówienia, które należą do kolejności #11000, oznacza te szczegóły zamówienia do usunięcia i przesyła te zmiany do bazy danych.

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a>Przykład

W tym drugim przykładzie celem jest usunięcie zamówienia (#10250). Kod najpierw analizuje `OrderDetails` tabelę, aby sprawdzić, czy kolejność usuwania jest tam dostępna. Jeśli zamówienie ma elementy podrzędne, najpierw elementy podrzędne, a następnie zamówienie jest oznaczone do usunięcia. <xref:System.Data.Linq.DataContext>Umieszcza rzeczywiste usuwanie w prawidłowej kolejności, tak aby polecenia Delete wysyłane do bazy danych przestrzegać ograniczeń bazy danych.

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
- [Instrukcje: przypisywanie procedur składowanych na potrzeby wykonywania aktualizacji, wstawiania i usuwania (O/R Designer)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
