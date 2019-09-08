---
title: Tworzenie i przesyłanie zmian danych
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 18468c9a2018a28e85d87155d98b0853854013fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792962"
---
# <a name="making-and-submitting-data-changes"></a>Tworzenie i przesyłanie zmian danych

W tematach w tej sekcji opisano, jak wprowadzać i przesyłać zmiany do bazy danych oraz jak obsługiwać optymistyczne konflikty współbieżności.

> [!NOTE]
> Można przesłonić [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne metody `Insert`dla `Update`, i `Delete` operacji bazy danych. Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md).
>
> Deweloperzy korzystający z programu Visual Studio mogą opracowywać procedury składowane w tym samym celu przy użyciu Object Relational Designer.

## <a name="in-this-section"></a>W tej sekcji

[Instrukcje: Wstawianie wierszy do bazy danych](how-to-insert-rows-into-the-database.md) \
Opisuje sposób wstawiania wierszy w bazie danych przez dodanie obiektów do modelu obiektów.

[Instrukcje: Aktualizowanie wierszy w bazie danych](how-to-update-rows-in-the-database.md) \
Opisuje sposób aktualizacji wierszy w bazie danych przez aktualizowanie obiektów w modelu obiektów.

[Instrukcje: Usuwanie wierszy z bazy danych](how-to-delete-rows-from-the-database.md) \
Opisuje sposób usuwania wierszy w bazie danych przez usunięcie obiektów w modelu obiektów.

[Instrukcje: Prześlij zmiany do bazy danych](how-to-submit-changes-to-the-database.md) \
Opisuje, w jaki sposób wysyłać zmiany modelu obiektów do bazy danych programu.

[Instrukcje: Przeprzesyłanie danych w nawiasach przy użyciu transakcji](how-to-bracket-data-submissions-by-using-transactions.md) \
Opisuje sposób dołączania operacji w transakcji.

[Instrukcje: Dynamiczne tworzenie bazy danych](how-to-dynamically-create-a-database.md) \
Opisuje sposób dynamicznego generowania baz danych oraz typowe scenariusze tego podejścia.

[Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md) \
Opisuje techniki rozwiązywania optymistycznych problemów współbieżności.
