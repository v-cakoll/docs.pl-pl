---
title: Migracja z programu .NET Framework 1.1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d54fac935e7b1fad6b07a3a6cf2031dbca702cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-from-the-net-framework-11"></a>Migracja z programu .NET Framework 1.1
[!INCLUDE[win7](../../../includes/win7-md.md)]i nowszych wersjach systemu operacyjnego Windows nie obsługują [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. W związku z tym aplikacje których docelowe [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] nie będzie działać bez żadnych modyfikacji na [!INCLUDE[win7](../../../includes/win7-md.md)] lub nowsze wersje systemu operacyjnego. W tym temacie omówiono kroki wymagane do uruchomienia aplikacji, którego element docelowy [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] w obszarze [!INCLUDE[win7](../../../includes/win7-md.md)] i nowszych wersjach systemu operacyjnego Windows. Aby uzyskać więcej informacji na temat [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] i [!INCLUDE[win8](../../../includes/win8-md.md)], zobacz [systemem 1.1 aplikacji programu .NET Framework w systemie Windows 8 i nowszych wersjach](../../../docs/framework/install/run-net-framework-1-1-apps.md).  
  
## <a name="retargeting-or-recompiling"></a>Przekierowania lub ponownej kompilacji  
 Istnieją dwa sposoby uzyskania aplikacji, która została skompilowana przy użyciu [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] do uruchamiania na [!INCLUDE[win7](../../../includes/win7-md.md)] lub nowszego systemu operacyjnego Windows:  
  
-   Można przekierować aplikację do działania w obszarze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Przekierowania wymaga dodania [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu do pliku konfiguracji aplikacji, który pozwala na uruchamianie jej w obszarze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Plik konfiguracji ma następującą postać:  
  
    ```xml  
    <configuration>   
       <startup>  
          <supportedRuntime version="v4.0"/>  
       </startup>  
    </configuration>  
    ```  
  
-   Można ponownie skompilować aplikację z kompilatora, którego celem jest [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Jeśli używasz programu Visual Studio 2003 pierwotnie do opracowywania i Skompiluj rozwiązanie, możesz otworzyć rozwiązanie w [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] i użyj **zgodność projektu** okno dialogowe, aby przekonwertować pliki rozwiązań i projektów z formatów używanych przez Program Visual Studio 2003 do formatu Microsoft kompilacji Engine (MSBuild) używanego przez [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)].  
  
 Niezależnie od tego, czy chcesz ponownie skompilować lub Przekieruj aplikację należy określić, czy aplikacja jest wpływ na wszystkie zmiany wprowadzone w nowszych wersjach systemu .NET Framework. Te zmiany są dwa rodzaje:  
  
-   Fundamentalne zmiany, które wystąpiły między [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] i nowszych wersjach systemu .NET Framework.  
  
-   Typy i elementy członkowskie typu, które zostały oznaczone jako przestarzałe lub przestarzałe między [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] i nowszych wersjach systemu .NET Framework.  
  
 Przekieruj aplikację lub ponownie go skompilować, należy przejrzeć zarówno zmiany podziału i przestarzałe typy i elementy członkowskie dla każdej wersji programu .NET Framework, która została opublikowana po [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
## <a name="breaking-changes"></a>Fundamentalne zmiany  
 Gdy wystąpi na istotne zmiany, w zależności od określonych zmian, obejście tego problemu mogą być dostępne zarówno dla przekierować i ponownie kompilowana aplikacji. W niektórych przypadkach można dodać elementu podrzędnego do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) elementu w pliku konfiguracji aplikacji, aby przywrócić poprzednich zachowanie. Na przykład następujący plik konfiguracyjny przywraca zachowanie sortowania i porównywania ciągów używane w [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] i mogą być używane z retargeted lub ponownej kompilacji aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
 W niektórych przypadkach mogą mieć do modyfikowania kodu źródłowego i ponownie skompilować aplikację.  
  
 Aby ocenić wpływ zmian najważniejszych możliwości w swojej aplikacji, należy przejrzeć następujące listy zmian:  
  
-   [Fundamentalne zmiany w programie .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=125263) dokumentów zmiany w [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] które mogą wpływać na aplikację, która dotyczy [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
-   [Zmiany w programie .NET Framework 3.5 z dodatkiem SP1](http://go.microsoft.com/fwlink/?LinkID=186989) dokumentów zmiany między [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] i [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].  
  
-   [.NET framework 4 migracji problemów](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) dokumentów zmiany między [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] i [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
## <a name="obsolete-types-and-members"></a>Przestarzałe typy i elementy członkowskie  
 Wpływ przestarzałe typy i składniki różni się nieco przekierować aplikacje i ponownie kompilowana aplikacji. Przestarzałe typy i elementy członkowskie nie wpłynie retargeted aplikacji, chyba że przestarzałego typu lub elementu członkowskiego został fizycznie usunięty z jej zestawu. Ponowną kompilację aplikacji, która zwykle używa przestarzałe typy i elementy Członkowskie tworzy kompilatora ostrzeżenie zamiast błędu kompilatora. Jednak w niektórych przypadkach generuje błąd kompilatora i kod, który używa przestarzałego typu lub elementu członkowskiego nie kompiluje się pomyślnie. W takim przypadku muszą zmodyfikować kod źródłowy, który wywołuje przestarzałego typu lub elementu członkowskiego, zanim zostanie ponownie skompilować aplikację. Aby uzyskać więcej informacji na temat przestarzałe typy i elementy członkowskie, zobacz [co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md).  
  
 Aby ocenić wpływ typy i składniki, które są przestarzałe począwszy od systemu [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], zobacz [co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md). Przejrzyj listę przestarzałe typy i element członkowski [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]i [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].
