---
title: "Procedurach przepływów pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e8f517b68695457c2819612bbd092b5ea03c5f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="procedural-workflows"></a>Procedurach przepływów pracy
Procedurach przepływów pracy za pomocą metod sterowanie przepływem podobne do tych w procedurach języków. Konstrukcje te obejmują `While` i `If`. Te przepływy pracy mogą być za darmo składane, takich jak przy użyciu innych działań kontroli przepływu <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Sterowanie przepływem wykonywania  
 Biblioteka działań przepływu pracy ma działania dla większości metod sterowanie przepływem używana w procedurach języków modelowania. Należą do nich następujące elementy:  
  
-   <xref:System.Activities.Statements.While>  
  
-   <xref:System.Activities.Statements.DoWhile>  
  
-   <xref:System.Activities.Statements.ForEach%601>  
  
-   <xref:System.Activities.Statements.Parallel>  
  
-   <xref:System.Activities.Statements.ParallelForEach%601>  
  
-   <xref:System.Activities.Statements.If>  
  
-   <xref:System.Activities.Statements.Switch%601>  
  
-   <xref:System.Activities.Statements.Pick>  
  
 Aby użyć działania przepływu sterowania, przeciągnij i upuść je z **działania** przybornika do działania złożonego wewnątrz okna projektanta.  
  
> [!NOTE]
>  Jeśli przy użyciu [!INCLUDE[dublin](../../../includes/dublin-md.md)] do przepływów pracy hosta na farmie sieci Web AppFabric przeniesie wystąpień między różnymi serwerami AppFabric. Wymaga to, że zasoby mogą być współużytkowane przez wszystkie węzły.  Żaden z domyślnych działań przepływu pracy NET 4 nie zawiera żadnych operacji, które uzyskują dostęp do zasobów lokalnych. Ponieważ AppFabric nie oferuje dowolny mechanizm można oznaczyć jako nieruchomości przepływu pracy, Projektant nie należy utworzyć niestandardowych działań, które się nie powieść, gdy przepływ pracy zostanie przesunięty.  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat blokowy przepływów pracy](../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)
