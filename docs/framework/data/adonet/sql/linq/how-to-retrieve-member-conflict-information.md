---
title: 'Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 478781e6c8ee31ebf6f5edd0e243a81d9e0524f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669565"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego
Możesz użyć <xref:System.Data.Linq.MemberChangeConflict> klasy do pobrania informacji o poszczególnych elementów członkowskich w konflikcie. W tym samym kontekście możesz podać niestandardową obsługę konfliktu dla dowolnego elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: Omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje iterację przez <xref:System.Data.Linq.ObjectChangeConflict> obiektów. Dla każdego obiektu, następnie iteruje <xref:System.Data.Linq.MemberChangeConflict> obiektów.  
  
> [!NOTE]
>  Obejmują <xref:System.Reflection> zapewnić <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacji.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
