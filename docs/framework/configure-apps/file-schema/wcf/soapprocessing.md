---
title: '&lt;soapProcessing&gt;'
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 296993f1a91a6da93f01610357f35dac4cfab9e6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210151"
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Definiuje zachowanie punktu końcowego klienta, które są używane do organizowania wiadomości między typami inne powiązanie i wersje komunikatów.

**\<System. ServiceModel >**   
&nbsp;&nbsp;**\<zachowania >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<zachowanie >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>Składnia

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|                   | Opis |
| ----------------- | ----------- |
| `processMessages` | Wartość logiczna określająca, czy komunikaty powinny być wprowadzane między wersjami komunikatu protokołu SOAP. |

### <a name="child-elements"></a>Elementy podrzędne

Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<zachowanie >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Określa zachowanie punktu końcowego. |

## <a name="remarks"></a>Uwagi

Przetwarzanie protokołu SOAP jest proces, w której wiadomości są konwertowane między wersjami wiadomości.

Usługa routingu Windows Communication Foundation (WCF) można przekonwertować komunikaty z jednego protokołu do innego. Jeśli wersje komunikatów przychodzących i wychodzących są różne, zostanie utworzony nowy komunikat poprawnej wersji. Przetwarzanie komunikatów z jednego <xref:System.ServiceModel.Channels.MessageVersion> do innego odbywa się przez utworzenie nowych wiadomości WCF, która zawiera część treści i odpowiednie nagłówki z przychodzących wiadomości WCF. Nagłówki specyficznych dla adresowania lub które są zrozumiałe na poziomie routera, nie są używane podczas tworzenia nowej wiadomości WCF, ponieważ te nagłówki są w innej wersji (w przypadku adresowania nagłówków) lub są przetwarzane jako część Komunikacja między klientem i router.

Czy nagłówek jest umieszczany w wiadomości wychodzących jest określany przez Określa, czy została ona oznaczona jako rozumieć przeszła przychodzący warstwy kanału. Nagłówki, które nie są zrozumiałe (takie jak niestandardowe nagłówki) nie są usuwane, a więc przekazać za pośrednictwem usługi routingu, są kopiowane do wiadomości wychodzących. Treść komunikatu jest kopiowane do wiadomości wychodzących. Komunikat zostanie przesłany limit ruchu wychodzącego kanału, w tym momencie wszystkie nagłówki i innych danych koperty określone na komunikat zostanie utworzona i dodać protokół/transportu.

Tych kroków przetwarzania ma miejsce, gdy określona jest zachowanie przetwarzania protokołu SOAP. To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowanie jest zachowanie punktu końcowego, która jest stosowana do wszystkich punktów końcowych klienta (wychodzące), podczas uruchamiania usługi routingu. Domyślnie [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie tworzy i dołącza nowe [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowania przy użyciu `processMessages` równa `true` dla każdego punkt końcowy klienta. Jeśli protokół, który usługa routingu nie zrozumieć, lub chcesz zastąpić domyślne zachowanie przetwarzania, możesz wyłączyć przetwarzania dla całej usługi routingu lub tylko dla konkretnego punktów końcowych protokołu SOAP.  Aby wyłączyć przetwarzania dla całej usługi routingu dla wszystkich punktów końcowych protokołu SOAP, ustaw `soapProcessing` atrybutu [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie `false`. Aby wyłączyć funkcję przetwarzania dla danego punktu końcowego protokołu SOAP, użyj tego zachowania i ustaw jego `processMessages` atrybutu `false`, następnie dołączyć to zachowanie punktu końcowego nie ma domyślnego przetwarzania kodu w.  Gdy [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie konfiguruje usługę routingu, zostanie pominięta, ponowne zastosowanie zachowanie punktu końcowego, ponieważ już istnieje.
