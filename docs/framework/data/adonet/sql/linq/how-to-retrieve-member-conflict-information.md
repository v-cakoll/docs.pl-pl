---
title: 'Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928632"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego
Za pomocą <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacje o konflikcie poszczególnych członków. W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla każdego elementu członkowskiego. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje iterację <xref:System.Data.Linq.ObjectChangeConflict> obiektów. Dla każdego obiektu, następnie iteruje za pomocą <xref:System.Data.Linq.MemberChangeConflict> obiektów.  
  
> [!NOTE]
> Uwzględnij <xref:System.Reflection> , aby podać <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacje.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
