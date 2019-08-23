---
title: Proceduralne przepływy pracy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: d1edd73b2276d0a3918b61c8da2d04769d09e7c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956118"
---
# <a name="procedural-workflows"></a>Proceduralne przepływy pracy
Proceduralne przepływy pracy używają metod sterowania przepływem podobnych do tych, które znajdują się w językach proceduralnych. Te konstrukcje obejmują `While` i `If`. Te przepływy pracy mogą być swobodnie składane przy użyciu innych działań <xref:System.Activities.Statements.Flowchart> sterowania <xref:System.Activities.Statements.Sequence>przepływem, takich jak i.  
  
## <a name="controlling-execution-flow"></a>Sterowanie przepływem wykonywania  
 Biblioteka działań przepływu pracy ma działania dotyczące modelowania większości metod kontroli przepływu używanych w językach proceduralnych. Należą do nich następujące elementy:  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Aby korzystać z działań sterowania przepływem, przeciągnij i upuść je z przybornika **działań** do działania złożonego wewnątrz okna projektanta.  
  
> [!NOTE]
> W przypadku używania funkcji hostingu systemu Windows Server AppFabric do hostowania przepływów pracy w kolektywie serwerów, program AppFabric przeniesie wystąpienia między różnymi serwerami programu AppFabric. Wymaga to, aby zasoby mogły być współużytkowane między wszystkimi węzłami.  Żadna z domyślnych działań w ramach przepływu pracy netto 4 nie zawiera żadnych operacji, które uzyskują dostęp do zasobów lokalnych. Ponieważ program AppFabric nie oferuje żadnego mechanizmu, aby oznaczyć przepływ pracy jako nieruchomy, Deweloper nie może tworzyć działań niestandardowych, które kończą się niepowodzeniem podczas przenoszenia przepływu pracy.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływy pracy schematów blokowych](flowchart-workflows.md)
