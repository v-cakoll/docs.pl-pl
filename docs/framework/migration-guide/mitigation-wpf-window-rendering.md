---
title: 'Ograniczenie: renderowanie okien WPF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 032d07b75b96809ff71c7735a267a7351ad25dda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-window-rendering"></a>Ograniczenie: renderowanie okien WPF
W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] działa w systemie Windows 8 i nowszym, całe okno jest renderowany bez przycinania, gdy wykraczał poza pojedynczy wyświetlana w przypadku wielu monitora.  
  
## <a name="impact"></a>Wpływ  
 Ogólnie rzecz biorąc renderowania całe okno na wiele monitorów bez wycinka jest oczekiwane zachowanie. Jednak na system Windows 7 i wcześniejsze wersje systemu windows WPF są kadrowane, gdy one wykraczać poza pojedynczy wyświetlania, ponieważ renderowanie części okna na drugim monitorze ma wpływ na wydajność znaczących.  
  
 Dokładne wpływ renderowanie okien WPF na monitorów w systemie Windows 8 lub nowszym nie jest dokładnie wymierne, ponieważ zależy od wielu czynników. W niektórych przypadkach mogą go nadal dawać niekorzystny wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiania aplikacji z dużą ilością grafiki i czy masz system windows międzystrefowymi monitorów. W pozostałych przypadkach po prostu można zachowanie spójności między wersje programu .NET Framework.  
  
## <a name="mitigation"></a>Ograniczenie  
 Można wyłączyć tę zmianę i powrócić do poprzedniej zachowanie wycinka okna WPF, gdy wykraczał poza jednym wyświetlania. Istnieją dwa sposoby wykonania tej czynności:  
  
-   Dodając `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` sekcji pliku konfiguracji aplikacji, można wyłączyć lub włączyć to zachowanie na aplikacje działające w systemie Windows 8 lub nowszym. Na przykład następującą sekcję konfiguracji wyłącza renderowanie bez wycinka:  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` Ustawienie konfiguracji może mieć jedną z dwóch wartości:  
  
    -   `true`, aby włączyć wycinka systemu windows do monitorowania granic podczas renderowania.  
  
    -   `false`, aby wyłączyć obcinanie do systemu windows do monitorowania granic podczas renderowania.  
  
-   Przez ustawienie <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwości `true` podczas uruchamiania aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
