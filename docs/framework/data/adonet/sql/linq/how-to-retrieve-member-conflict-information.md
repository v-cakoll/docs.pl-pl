---
title: 'Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793304"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego
Za pomocą <xref:System.Data.Linq.MemberChangeConflict> klasy można pobrać informacje o konflikcie poszczególnych członków. W tym samym kontekście można zapewnić niestandardową obsługę konfliktu dla każdego elementu członkowskiego. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod wykonuje iterację <xref:System.Data.Linq.ObjectChangeConflict> obiektów. Dla każdego obiektu, następnie iteruje za pomocą <xref:System.Data.Linq.MemberChangeConflict> obiektów.  
  
> [!NOTE]
> Uwzględnij <xref:System.Reflection> , aby podać <xref:System.Data.Linq.MemberChangeConflict.Member%2A> informacje.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
