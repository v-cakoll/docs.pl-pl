---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936446"
---
# <a name="serviceactivations"></a>\<> ServiceActivations

Element konfiguracji, który pozwala dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które są mapowane na typy usług Windows Communication Foundation (WCF). Dzięki temu można aktywować usługi hostowane w usłudze WAS lub IIS bez pliku SVC.

\<system.ServiceModel>\
\<serviceHostingEnvironment > \
\<> ServiceActivations

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

Należy pamiętać `<serviceHostingEnvironment>` , że jest to konfiguracja poziomu aplikacji. Należy umieścić `web.config` zawiera konfigurację w katalogu głównym aplikacji wirtualnej. Ponadto `serviceHostingEnvironment` jest sekcją dziedziczną machineToApplication. Po zarejestrowaniu pojedynczej usługi w katalogu głównym maszyny każda usługa w aplikacji będzie dziedziczyć tę usługę.

Aktywacja oparta na konfiguracji obsługuje aktywację za pośrednictwem protokołu HTTP i innego niż http. Wymaga rozszerzeń w relativeAddress (SVC, xoml lub. xamlx). Możesz zmapować własne rozszerzenia na buildProviders, które następnie umożliwią aktywację usługi w dowolnym rozszerzeniu. W `<serviceActivations>` przypadku konfliktu sekcja zastępuje rejestracje SVC.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
