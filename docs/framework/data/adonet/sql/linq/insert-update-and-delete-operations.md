---
title: Operacje wstawiania, aktualizowania i usuwania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793058"
---
# <a name="insert-update-and-delete-operations"></a>Operacje wstawiania, aktualizowania i usuwania

Wykonujesz `Insert`operacje `Update`, i `Delete` w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , przez dodawanie, zmienianie i usuwanie obiektów w modelu obiektów. Domyślnie program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy akcje na SQL i przesyła zmiany do bazy danych.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferuje maksymalną elastyczność w zakresie manipulowania i utrwalania zmian wprowadzonych w obiektach. Gdy tylko obiekty jednostek są dostępne (pobierając je za pomocą zapytania lub przez zbudowanie ich nową), można je zmienić jako typowe obiekty w aplikacji. Oznacza to, że można zmienić ich wartości, można dodać je do kolekcji i usunąć je z kolekcji. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]śledzi zmiany i jest gotowy do przesyłania ich z powrotem do bazy danych podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje ani nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz w tabeli zawierającej ograniczenia, musisz ustawić `ON DELETE CASCADE` regułę w ograniczeniu klucza obcego w bazie danych lub użyć własnego kodu, aby najpierw usunąć obiekty podrzędne, które uniemożliwiają usunięcie obiektu nadrzędnego. W przeciwnym razie jest zgłaszany wyjątek. Aby uzyskać więcej informacji, zobacz [jak: Usuń wiersze z bazy danych](how-to-delete-rows-from-the-database.md).

Poniższe fragmenty używają `Customer` klas i `Order` z przykładowej bazy danych Northwind. Definicje klas nie są wyświetlane dla zwięzłości.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

Gdy jest wywoływana <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program automatycznie generuje i wykonuje polecenia SQL wymagane przez program, aby przesłać zmiany z powrotem do bazy danych.

> [!NOTE]
> To zachowanie można zastąpić za pomocą własnej logiki niestandardowej, zazwyczaj w drodze procedury składowanej. Aby uzyskać więcej informacji, zobacz [obowiązki dewelopera w celu przesłania domyślnego zachowania](responsibilities-of-the-developer-in-overriding-default-behavior.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą w tym celu opracowywać procedury składowane za pomocą Object Relational Designer.

## <a name="see-also"></a>Zobacz także

- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md)
