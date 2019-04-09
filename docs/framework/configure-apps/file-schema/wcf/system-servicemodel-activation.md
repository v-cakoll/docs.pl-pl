---
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: b29f7173b4d75ec9adff37449d3d56266f01a03c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196193"
---
# <a name="systemservicemodelactivation"></a><span data-ttu-id="764c7-102">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="764c7-102">\<system.serviceModel.activation></span></span>
<span data-ttu-id="764c7-103">Ta sekcja konfiguracji reprezentuje ustawienia konfiguracji dla narzędzia SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="764c7-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="764c7-104">Elementy konfiguracji można skonfigurować w pliku pliku konfiguracyjnego SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="764c7-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="764c7-105">W szczególności zawiera wszystkie ustawienia dla komputera, które muszą być skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="764c7-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="764c7-106">Przykładowy plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="764c7-106">Sample Configuration File</span></span>  
 <span data-ttu-id="764c7-107">Oto przykładowy plik konfiguracji (pliku konfiguracyjnego SMSvcHost.exe.config), który jest używany przez proces odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="764c7-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="764c7-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="764c7-108">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>
