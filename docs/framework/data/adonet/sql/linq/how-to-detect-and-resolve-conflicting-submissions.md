---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940096"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferuje wiele zasobów do wykrywania i rozwiązywania konfliktów, które pochodzą od zmian wielu użytkowników w bazie danych. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)zmian.  
  
## <a name="example"></a>Przykład  
 Poniższy `try` przykład pokazuje / <xref:System.Data.Linq.ChangeConflictException> blok, który przechwytuje wyjątek. `catch` Informacje o jednostkach i elementach członkowskich dla każdego konfliktu są wyświetlane w oknie konsoli.  
  
> [!NOTE]
> Musisz dołączyć `using System.Reflection` dyrektywę (`Imports System.Reflection` w Visual Basic) do obsługi pobierania informacji. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
