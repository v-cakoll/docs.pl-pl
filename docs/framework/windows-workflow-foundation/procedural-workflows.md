---
title: Proceduralne przepływy pracy
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 15ff155fb057c4c10663d383a8942108c6e4375c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348367"
---
# <a name="procedural-workflows"></a>Proceduralne przepływy pracy
Proceduralne przepływy pracy za pomocą metod sterowanie przepływem podobne do tych w procedurach językach. Te konstrukcje obejmują `While` i `If`. Te przepływy pracy mogą być swobodnie składane, przy użyciu innych działań sterowania przepływem, takich jak <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Sequence>.  
  
## <a name="controlling-execution-flow"></a>Sterowanie przepływem wykonania  
 Biblioteka działań przepływu pracy ma działania dla większości metod sterowanie przepływem używanych w procedurach językach modelowania. Należą do nich następujące elementy:  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 Aby użyć działania sterowania przepływem, przeciągnij i upuść je z **działania** przybornika do działania złożonego wewnątrz okna projektanta.  
  
> [!NOTE]
>  Jeśli używane funkcje hostingu programu Windows Server AppFabric hosta przepływów pracy w ramach farmy sieci Web, AppFabric zostanie przesunięty wystąpień między różnymi serwerami AppFabric. Wymaga to, że zasoby mogą być współużytkowane przez wszystkie węzły.  Brak domyślnych działań przepływu pracy NET 4 zawierać dowolne operacje wymagające dostępu do zasobów lokalnych. Ponieważ AppFabric nie oferuje żadnych mechanizm zaznaczania przepływów pracy jako nieruchome, deweloper nie należy utworzyć niestandardowe działania, które się nie powieść, gdy przepływ pracy zostanie przeniesiony.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływy pracy schematów blokowych](flowchart-workflows.md)
