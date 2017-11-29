---
title: '&lt;add&gt; w &lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5166f7859bb3e914de8313de08427cda9bc06d6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;add&gt; w &lt;serviceActivations&gt;
Element konfiguracji, który można zdefiniować ustawienia Aktywacja usług wirtualnych mapowane na Twojej [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typów usług. Dzięki temu można aktywować usługi hostowane w WAS / usług IIS bez pliku svc.  
  
 \<System. ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Fabryka|Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.|  
|usługa|Typ ServiceType, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótkich Typename (gdy jest on umieszczany w folderze App_Code).|  
|Element relativeAddress|Adres względny w bieżącej aplikacji usług IIS — na przykład "Service.svc". Ten adres względny WCF 4.0 musi zawierać jedno z rozszerzeń plików znanych (SVC, .xamlx,...). Nie pliku fizycznego musi istnieć dla relativeUrl|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Sekcja konfiguracyjna, który opisuje ustawienia aktywacji.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższy przykład przedstawia sposób konfigurowania ustawień aktywacji w pliku web.config.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 Za pomocą tej konfiguracji, można uaktywnić GreetingService bez użycia pliku svc.  
  
 Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji. Należy umieścić `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej. Ponadto `serviceHostingEnvironment` jest sekcją dziedziczne machinetoApplication. Jeśli zarejestrujesz pojedynczą usługę w katalogu głównym komputera każdej usługi w aplikacji będzie dziedziczyć tej usługi.  
  
 Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http. Wymaga to rozszerzenia w relatativeAddress, tj. SVC, xoml lub .xamlx. Należy mapować własne rozszerzenia buildProviders wiedzieć, który następnie umożliwi aktywowania usługi przez dowolnego rozszerzenia. Po konflikt `<serviceActivations>` sekcji zastępuje .svc rejestracji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
