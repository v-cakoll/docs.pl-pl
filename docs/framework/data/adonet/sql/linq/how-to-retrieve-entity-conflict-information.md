---
title: 'Instrukcje: Pobieranie informacji o konflikcie jednostki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 766ede90b14f07e2799c2715daf62aaeeeaa83f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782239"
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Instrukcje: Pobieranie informacji o konflikcie jednostki
Możesz użyć obiektów klasy, <xref:System.Data.Linq.ObjectChangeConflict> aby podać informacje o konfliktach ujawnionych przez <xref:System.Data.Linq.ChangeConflictException> wyjątki. Aby uzyskać więcej informacji, [Zobacz optymistyczne współbieżność: Przegląd](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje iterację przez listę skumulowanych konfliktów.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Zarządzanie konfliktami zmian](how-to-manage-change-conflicts.md)
