---
title: 'Środki zaradcze: Renderowanie okien WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71e1829716e0a9d5fc63692ca84c8bfefe4cefef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663469"
---
# <a name="mitigation-wpf-window-rendering"></a>Środki zaradcze: Renderowanie okien WPF
W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] działa w systemie Windows 8 i nowszych, całe okno jest renderowany bez przycinania, gdy wykraczał poza jednym wyświetlana w przypadku wielu monitorów.  
  
## <a name="impact"></a>Wpływ  
 Ogólnie rzecz biorąc renderowanie całe okno na wiele monitorów bez przycinania to oczekiwane zachowanie. Jednak na Windows 7 i starszych wersjach, WPF, windows powoduje ich rozszerzania poza pojedynczy ekran, ponieważ renderowanie części okna na drugim monitorze ma wpływ na wydajność znaczące.  
  
 Dokładne wpływ renderowanie okien WPF na monitorów w systemie Windows 8 lub nowszym nie jest dokładnie wymierne, ponieważ zależy od wielu czynników. W niektórych przypadkach go może dać nadal niekorzystny wpływ na wydajność, szczególnie w przypadku użytkowników, którzy uruchamiania aplikacji intensywnie korzystających z grafiki i czy masz system windows międzystrefowymi monitorów. W innych przypadkach może po prostu chcesz spójne zachowanie różnych wersji programu .NET Framework.  
  
## <a name="mitigation"></a>Ograniczenie  
 Można wyłączyć tej zmiany i powrócić do poprzedniego zachowania przycinania okna WPF, gdy wykraczał poza pojedynczy ekran. Istnieją dwa sposoby wykonania tej czynności:  
  
-   Dodając `<EnableMultiMonitorDisplayClipping>` elementu `<appSettings>` sekcję pliku konfiguracji aplikacji można wyłączyć lub włączyć to zachowanie w aplikacje działające w systemie Windows 8 lub nowszym. Na przykład w poniższej sekcji konfiguracji wyłącza renderowanie, bez przycinania:  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` Ustawienie konfiguracji może mieć jedną z dwóch wartości:  
  
    -   `true`, aby umożliwić wycinka monitorowania granic podczas renderowania w systemie windows.  
  
    -   `false`, aby wyłączyć obcinanie do systemu windows do monitorowania granic podczas renderowania.  
  
-   Ustawiając <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> właściwości `true` przy uruchamianiu aplikacji.  
  
## <a name="see-also"></a>Zobacz także
- [Zmiany środowiska uruchomieniowego](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
