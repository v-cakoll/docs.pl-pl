---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 12369f1053638583a3864fab396869d0e7045732
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918678"
---
# <a name="transactedbatching"></a>\<transactedBatching >

Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.

\<system.ServiceModel>\
\<zachowania > \
\<endpointBehaviors>\
\<zachowanie > \
\<transactedBatching >

## <a name="syntax"></a>Składnia

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`maxBatchSize`|Liczba całkowita określająca maksymalną liczbę operacji odbioru, które mogą być przetwarzane wsadowo w jednej transakcji. Wartość domyślna to 0.|

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|

## <a name="remarks"></a>Uwagi

Transport, który jest skonfigurowany z przetwarzaniem wsadowym transakcji, próbuje wsadowo wykonać kilka operacji odbioru w jednej transakcji. Dzięki temu można uniknąć stosunkowo wysokiego kosztu tworzenia transakcji i zatwierdzania jej w każdej operacji odbierania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać działanie transakcyjnego przetwarzania wsadowego do usługi w pliku konfiguracji.

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
