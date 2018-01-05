---
title: "Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28dba94262002f863a750a83493ba98b3714fabd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Porady: wykrywanie i rozwiązać powodujące konflikt przesłanych
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]udostępnia wiele zasobów wykrywania i rozwiązywania konfliktów, które wynikają z wielu użytkowników zmian w bazie danych. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `try` / `catch` bloku, który przechwytuje <xref:System.Data.Linq.ChangeConflictException> wyjątku. Informacje o wszystkich konfliktów jednostki i element członkowski jest wyświetlany w oknie konsoli.  
  
> [!NOTE]
>  Należy uwzględnić `using System.Reflection` — dyrektywa (`Imports System.Reflection` w języku Visual Basic) do obsługi pobierania informacji. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
