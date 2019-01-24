---
title: '&lt;system.serviceModel.activation&gt;'
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: 10496b9624e1edb044187c08c9dfac0b852fe490
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666354"
---
# <a name="ltsystemservicemodelactivationgt"></a><span data-ttu-id="38c77-102">&lt;system.serviceModel.activation&gt;</span><span class="sxs-lookup"><span data-stu-id="38c77-102">&lt;system.serviceModel.activation&gt;</span></span>
<span data-ttu-id="38c77-103">Ta sekcja konfiguracji reprezentuje ustawienia konfiguracji dla narzędzia SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="38c77-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="38c77-104">Elementy konfiguracji można skonfigurować w pliku pliku konfiguracyjnego SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="38c77-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="38c77-105">W szczególności zawiera wszystkie ustawienia dla komputera, które muszą być skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="38c77-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="38c77-106">Przykładowy plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="38c77-106">Sample Configuration File</span></span>  
 <span data-ttu-id="38c77-107">Oto przykładowy plik konfiguracji (pliku konfiguracyjnego SMSvcHost.exe.config), który jest używany przez proces odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="38c77-107">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38c77-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38c77-108">See also</span></span>
- <xref:System.ServiceModel.Activation.Configuration>
