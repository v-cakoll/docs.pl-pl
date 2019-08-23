---
title: <add> dla <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920030"
---
# <a name="add-of-serviceactivations"></a>\<Dodaj >ę \<ServiceActivations >

Element konfiguracji, który pozwala zdefiniować ustawienia aktywacji usługi wirtualnej, które są mapowane na typy usług Windows Communication Foundation (WCF). Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.

\<system.ServiceModel>\
\<serviceHostingEnvironment>

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
|indywidual|Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.|
|usługa|Typ, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótki typ TypeName (gdy jest umieszczony w folderze App_Code).|
|relativeAddress|Adres względny w bieżącej aplikacji usług IIS — na przykład "Service. svc". W programie WCF 4,0 ten adres względny musi zawierać jedno z znanych rozszerzeń plików (. svc,. xamlx,...). Brak pliku fizycznego dla relativeUrl|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Sekcja konfiguracji opisująca ustawienia aktywacji.|

## <a name="remarks"></a>Uwagi

Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku Web. config.

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

Korzystając z tej konfiguracji, można aktywować GreetingService bez użycia pliku SVC.

Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji. Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej. Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication. Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.

Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http. Wymaga rozszerzeń w relativeAddress, tzn. svc, xoml lub. xamlx. Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu. W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
