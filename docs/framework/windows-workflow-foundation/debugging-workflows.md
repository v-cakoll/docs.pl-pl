---
title: "Debugowanie przepływów pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9304622ff4243f7f885de2175a66cfae1c192aeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-workflows"></a>Debugowanie przepływów pracy
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]oferuje kilka opcji debugowania uruchomionych przepływów pracy ze środowiska projektowego. Przepływy pracy może być debugowany w projektancie, języka XAML i kodem.  
  
## <a name="debugging-in-the-workflow-designer"></a>Debugowanie w Projektancie przepływów pracy  
 Dla działań w Projektancie przepływów pracy można ustawić punktów przerwania albo wyróżnianie działania i naciskając klawisz **F9** lub za pomocą menu kontekstowe działania. Wykonywanie przepływu pracy, a następnie podziały po uruchomieniu hosta przepływu pracy w trybie debugowania. Na poniższym zrzucie ekranu wykonywania przepływu pracy została wstrzymana na punkt przerwania. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Debugowania przepływów pracy za pomocą projektanta przepływów pracy](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Debugowanie w XAML  
 Jeśli przepływ pracy został wstrzymany w punkcie przerwania w projektancie, również można debugować przepływ pracy w języku XAML. Aby wyświetlić punkt wykonywania w języku XAML, wybierz **widoku XAML** w Projektancie przepływów pracy podczas wykonywania przepływu pracy zostało wstrzymane. Debugowanie można przełączyć do projektanta przez ponowne otwarcie przepływu pracy w Projektancie z Eksploratora rozwiązań. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Porady: debugowanie XAML z projektanta przepływów pracy](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Debugowanie w kodzie  
 Punkty przerwania kodu mogą być używane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] w taki sam sposób mogą być używane w innych aplikacjach imperatywnych. Lewy margines okienka kod, aby utworzyć punkt przerwania kodu, kliknij lub naciśnij klawisz **F9** umieścić punkt przerwania w lokalizacji kursora.  
  
## <a name="attaching-to-a-workflow-process"></a>Dołączanie do procesu przepływu pracy  
 Debugowanie przepływu pracy również obsługuje przy użyciu infrastruktury programu Visual Studio, aby dołączyć do procesu. Dzięki temu autorem przepływu pracy, aby debugować przepływ pracy w środowisku inny host, takich jak Internet informacji Services (IIS) 7.0.  
  
## <a name="remote-debugging"></a>Debugowanie zdalne  
 [!INCLUDE[wf](../../../includes/wf-md.md)]debugowanie zdalne działa tak samo, jak zdalnego debugowania dla innych [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] składników. Informacje na temat używania zdalnego debugowania, zobacz [porady: Włączanie debugowania zdalnego](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Jeśli aplikacja przepływu pracy jest przeznaczony dla x86 architektury i znajduje się na komputerze z systemem 64-bitowym systemie operacyjnym, a następnie zdalne debugowanie nie będzie działać, chyba że [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] jest zainstalowany na komputerze zdalnym lub element docelowy dla aplikacji przepływ pracy zostanie zmieniona. Aby **dowolnego Procesora**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Rozszerzanie debugowania usługi przepływu pracy  
 Usługa debugera przepływu pracy jest obecnie publicznego i może służyć do tworzenia niestandardowych aplikacji, takich jak monitorowanie, symulacji i debugowania w Projektancie ponownie hostowanej. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.Activities.Presentation.Debug.DebuggerService> tematu.
