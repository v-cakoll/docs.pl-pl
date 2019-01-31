---
title: <add> z <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: e87a79137641d2697452a4862c5449da166ecfda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262679"
---
# <a name="add-of-serviceactivations"></a>\<Dodaj > z \<serviceActivations >
Element konfiguracji, który pozwala zdefiniować ustawienia Aktywacja usług wirtualnych mapowane odpowiadają typom usług Windows Communication Foundation (WCF). Dzięki temu można aktywować usługi hostowane w WAS / IIS bez pliku .svc.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Fabryka|Ciąg, który określa nazwę typu CLR fabryki, która generuje element aktywacji usługi.|  
|usługa|Typ ServiceType, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótki Typename (jeśli znajduje się w folderze App_Code).|  
|relativeAddress|Adres względny w bieżącej aplikacji usług IIS — na przykład "Service.svc". W wersji 4.0 WCF tego adresu względnego musi zawierać rozszerzenia znanych plików (.svc .xamlx...). Nie pliku fizycznego musi istnieć dla relativeUrl|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Sekcja konfiguracji, który opisuje ustawienia aktywacji.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku web.config.  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 Za pomocą tej konfiguracji, możesz aktywować GreetingService bez użycia pliku .svc.  
  
 Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji. Musisz umieszczać `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej. Ponadto `serviceHostingEnvironment` to sekcja dziedziczne machinetoApplication. Jeśli zarejestrujesz jednej usługi w katalogu głównym maszyny do każdej usługi w aplikacji będą dziedziczyć tę usługę.  
  
 Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http. Wymaga rozszerzenia w relatativeAddress, czyli .svc xoml oraz .xamlx. Własne rozszerzenia można zamapować na buildProviders wie, który następnie umożliwi Aktywuj usługę za pośrednictwem dowolnego rozszerzenia. Po konfliktu `<serviceActivations>` sekcji zastępuje .svc rejestracji.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
