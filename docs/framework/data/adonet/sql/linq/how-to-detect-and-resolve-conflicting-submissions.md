---
title: 'Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 606231449263f1c26596ca8606a88053c6aded8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138128"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udostępnia wiele zasobów do wykrywania i rozwiązywania konfliktów, które wynikają z wieloma użytkownikami zmian w bazie danych. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `try` / `catch` blok, który przechwytuje <xref:System.Data.Linq.ChangeConflictException> wyjątku. Informacje o wszystkich konfliktów jednostki i elementu członkowskiego jest wyświetlany w oknie konsoli.  
  
> [!NOTE]
>  Musi zawierać `using System.Reflection` — dyrektywa (`Imports System.Reflection` w języku Visual Basic) do obsługi pobierania informacji. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
