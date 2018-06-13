---
title: Przestarzałe typy w programie Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 899d21f23c0500a1df01916d1da210b2f9bea95b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512430"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Przestarzałe typy w programie Windows Workflow Foundation
W przypadku .NET 4 przepływu pracy zespołu wydawane wszystkich nowych aparatu przepływu pracy w <xref:System.Activities> przestrzeni nazw. Wraz z wydaniem .NET 4.5 w wersji Beta firma Microsoft oznaczenie większość typów w "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, i <xref:System.Workflow.Runtime> przestrzenie nazw jako przestarzałe.  
  
## <a name="obsolete-namespaces-and-tools"></a>Przestarzałe obszary nazw i narzędzia  
 Następujące zestawy są co najmniej jeden typ publiczny, które zostaną wycofane:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   WFC.exe  
  
 W związku z tym klienci korzystający z przestarzałe interfejsy API 3 WF wystąpi ostrzeżenia kompilacji z komunikatu podobnego do następującego:  
  
 **Ostrzeżenie BC40000: X jest przestarzała: WF 3 typy są przestarzałe. Zamiast tego użyj WF 4.** Typy zostanie usunięty z programu .NET Framework w przyszłej wersji, ale firma Microsoft nie ustalone jeszcze określonym czasie (nie w 4.5). Ten krok bieżącego umożliwia firmie Microsoft w celu komunikowania się z naszym kierunku naszym klientom i Zezwalaj dużo czasu, można przenieść do nowego modelu WF4. Firma Microsoft oczywiście będzie obsługującej te typy WF 3 w obszarze [firmy Microsoft obsługuje technicznego](http://aka.ms/MicrosoftSupportLifecycle). Istniejące aplikacje WF3 będą uruchamiane bez problemu na .NET 4.5 i [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] będzie obsługiwać nowych i istniejących rozwiązań opartych na WF3.  
  
 Zasady dotyczące typów w <xref:System.Workflow.Activities.Rules> przestrzeni nazw, które nie mają zastępczy w WF 4.5, nie są przestarzałe.  
  
 Klienci, którzy mają zostać poddane migracji aplikacji i WF 4 znajdziesz w Pomocy [wskazówek dotyczących migracji 4 przepływu pracy](migration-guidance.md).
