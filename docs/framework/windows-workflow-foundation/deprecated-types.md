---
title: Przestarzałe typy w programie Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: b25be26d4c0ad6c423b011cd7cad24a8728333f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658902"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Przestarzałe typy w programie Windows Workflow Foundation
W .NET 4 zespołu przepływu pracy zwolnione wszystkich nowych aparatu przepływu pracy w <xref:System.Activities> przestrzeni nazw. Wersja programu .NET 4.5 w wersji Beta firma Microsoft oznaczanie większość typów w "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, i <xref:System.Workflow.Runtime> przestrzeni nazw jako przestarzałe.  
  
## <a name="obsolete-namespaces-and-tools"></a>Przestarzałe przestrzenie nazw i narzędzia  
 Następujące zestawy mają jeden lub więcej typów publicznych, które staną się przestarzałe:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   WFC.exe  
  
 W rezultacie klienci, którzy używają przestarzałych API 3 WF będą napotykać ostrzeżenia kompilacji za pomocą komunikatu podobnego do następującego:  
  
 **Ostrzeżenie BC40000: X jest przestarzała: WF 3 typy są przestarzałe. Zamiast tego użyj WF 4.** Typy zostanie usunięty z programu .NET Framework w przyszłej wersji, ale nie Ustaliliśmy jeszcze tego przedziału czasu (nie w 4.5). Ten krok bieżącego pozwala nam komunikować się z naszym kierunek dla naszych klientów i zezwolić im na może zająć dużo czasu, aby przejść do nowego modelu WF4. Firma Microsoft oczywiście, będzie obsługiwać te typy WF 3 w obszarze [zasady świadczenia pomocy technicznej firmy Microsoft](https://aka.ms/MicrosoftSupportLifecycle). Istniejące aplikacje WF3 uruchomią się bez problemu w .NET 4.5 i [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] będzie obsługiwać nowych i istniejących rozwiązań opartych na WF3.  
  
 Zasady dotyczące typów w <xref:System.Workflow.Activities.Rules> przestrzeni nazw, które nie mają zastępuje w programie WF 4.5, nie są przestarzałe.  
  
 Klienci, którzy chcą przeprowadzić migrację aplikacji WF 4 znajdą się w Pomocy [wskazówek dotyczących migracji 4 przepływu pracy](migration-guidance.md).
