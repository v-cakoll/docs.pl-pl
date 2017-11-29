---
title: "Porady: pobieranie informacji konflikt elementu członkowskiego"
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
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a6766e40b842675cbe37ba1ebeb1a956c19e6318
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a>Porady: pobieranie informacji konflikt elementu członkowskiego
Można użyć <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacji o poszczególnych elementów w konflikt. W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla dowolnego elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod iteruje <xref:System.Data.Linq.ObjectChangeConflict> obiektów. Dla każdego obiektu ją następnie iteruje <xref:System.Data.Linq.MemberChangeConflict> obiektów.  
  
> [!NOTE]
>  Obejmują <xref:System.Reflection> zapewnić <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacji.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
