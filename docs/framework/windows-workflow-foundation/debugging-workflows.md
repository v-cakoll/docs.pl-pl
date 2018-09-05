---
title: Debugowanie przepływów pracy
ms.date: 03/30/2017
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
ms.openlocfilehash: 17cee1f1b509e777edd3f08c55d473d768b19b55
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660012"
---
# <a name="debugging-workflows"></a>Debugowanie przepływów pracy
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] oferuje kilka opcji do debugowania działania przepływów pracy ze środowiska projektowego. Przepływy pracy mogą być debugowane w projektancie, XAML i kodu.  
  
## <a name="debugging-in-the-workflow-designer"></a>Debugowanie w Projektancie przepływu pracy  
 W przypadku działań w Projektancie przepływu pracy można ustawić punktów przerwania, albo wyróżnianie działania i naciskając klawisz **F9** lub za pomocą menu kontekstowego tego działania. Wykonanie przepływu pracy, a następnie podziały po uruchomieniu hosta przepływu pracy w trybie debugowania. Poniższy zrzut ekranu wykonywania przepływu pracy zostało wstrzymane w punkcie przerwania. Aby uzyskać więcej informacji, zobacz [debugowanie przepływów pracy za pomocą projektanta przepływu pracy](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Debugowanie w XAML  
 Jeśli przepływ pracy został wstrzymany w punkcie przerwania w projektancie, również można debugować przepływ pracy w XAML. Zaznacz, aby wyświetlić punkty wykonywania w XAML **widok XAML** w Projektancie przepływu pracy podczas wykonywania przepływu pracy zostało wstrzymane. Debugowanie można dostosować do projektanta przez ponowne otwarcie przepływu pracy w Projektancie z poziomu Eksploratora rozwiązań. Aby uzyskać więcej informacji, zobacz [porady: debugowanie XAML za pomocą projektanta przepływu pracy](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Debugowanie w kodzie  
 Punkty przerwania w kodzie mogą być używane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w taki sam sposób, że mogą być używane w innych aplikacjach imperatywnego. Lewy margines okienka kodu, aby utworzyć punkt przerwania w kodzie, kliknij lub naciśnij **F9** umieścić punkt przerwania w lokalizacji kursora.  
  
## <a name="attaching-to-a-workflow-process"></a>Dołączanie do procesu przepływu pracy  
 Debugowanie przepływu pracy, również obsługuje przy użyciu infrastruktury programu Visual Studio, aby dołączyć do procesu. Dzięki temu autorem przepływu pracy, aby debugować przepływ pracy w środowisku inny host takich jak Internet informacji Services (IIS) 7.0.  
  
## <a name="remote-debugging"></a>Debugowanie zdalne  
 Zdalne debugowanie w Windows Workflow Foundation (WF) działa tak samo, jak zdalne debugowanie dla innych składników programu Visual Studio. Aby uzyskać informacje na temat korzystania z debugowania zdalnego, zobacz [porady: Włączanie debugowania zdalnego](https://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury, która jest hostowana na komputerze z systemem 64-bitowym systemie operacyjnym, zdalne debugowanie nie będzie działało, chyba że program Visual Studio jest zainstalowany na komputerze zdalnym lub obiekt docelowy dla aplikacji przepływu pracy jest zmieniana na **Dowolny procesor CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Rozszerzenie debugowania usługi przepływu pracy  
 Usługa przepływu pracy debugera jest obecnie dostępna publicznie i może służyć do tworzenia niestandardowych aplikacji, takich jak monitorowanie, symulowania i debugowania w Projektancie ponownie hostowanej. Aby uzyskać więcej informacji, zobacz <xref:System.Activities.Presentation.Debug.DebuggerService> tematu.
