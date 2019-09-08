---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 2de0182cc0b87768a9cff553b7ec6e77f8ccc7b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793777"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oferuje wiele zasobów do wykrywania i rozwiązywania konfliktów, które pochodzą od zmian wielu użytkowników w bazie danych. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami](how-to-manage-change-conflicts.md)zmian.  
  
## <a name="example"></a>Przykład  
 Poniższy `try` przykład pokazuje / <xref:System.Data.Linq.ChangeConflictException> blok, który przechwytuje wyjątek. `catch` Informacje o jednostkach i elementach członkowskich dla każdego konfliktu są wyświetlane w oknie konsoli.  
  
> [!NOTE]
> Musisz dołączyć `using System.Reflection` dyrektywę (`Imports System.Reflection` w Visual Basic) do obsługi pobierania informacji. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
