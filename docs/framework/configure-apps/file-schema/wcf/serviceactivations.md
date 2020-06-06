---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855133"
---
# \<serviceActivations>

Element konfiguracji, który pozwala dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które są mapowane na typy usług Windows Communication Foundation (WCF). Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

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

Brak.

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|Dodaje element konfiguracji, który określa aktywację aplikacji usługi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Definiuje typ tworzenia wystąpień środowiska hostingu usługi dla określonego transportu.|

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

Należy pamiętać, że `<serviceHostingEnvironment>` jest to konfiguracja poziomu aplikacji. Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej. Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication. Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.

Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http. Wymaga rozszerzeń w relativeAddress (SVC, xoml lub. xamlx). Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu. W przypadku konfliktu `<serviceActivations>` sekcja zastępuje rejestracje SVC.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
