---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 678b1f71ac15d3ad30df28cec5abbe403fb08c95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937050"
---
# <a name="soapprocessing"></a>\<soapProcessing >

Definiuje zachowanie punktu końcowego klienta używane do organizowania komunikatów między różnymi typami powiązań i wersjami komunikatów.

**\<system.ServiceModel>**    
&nbsp;&nbsp; **\<> zachowań**   
&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointBehaviors>**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zachowania**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing >**
  
## <a name="syntax"></a>Składnia  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
  
W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|                   | Opis |
| ----------------- | ----------- |
| `processMessages` | Wartość logiczna określająca, czy komunikaty powinny być organizowane między wersjami komunikatów SOAP. |

### <a name="child-elements"></a>Elementy podrzędne

Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [ **\<> zachowania**](behavior-of-endpointbehaviors.md) | Określa zachowanie punktu końcowego. |

## <a name="remarks"></a>Uwagi

Przetwarzanie protokołu SOAP to proces, w którym komunikaty są konwertowane między wersjami komunikatów.

Usługa routingu Windows Communication Foundation (WCF) umożliwia konwertowanie komunikatów z jednego protokołu na inny. Jeśli wersje wiadomości przychodzących i wychodzących są różne, zostanie utworzona nowa wiadomość o prawidłowej wersji. Przetwarzanie komunikatów z jednego <xref:System.ServiceModel.Channels.MessageVersion> do drugiego jest realizowane przez konstruowanie nowej wiadomości WCF zawierającej część treści i odpowiednich nagłówków z przychodzącego komunikatu WCF. Nagłówki, które są specyficzne dla adresowania lub które są zrozumiałe na poziomie routera, nie są używane podczas konstruowania nowej wiadomości WCF, ponieważ te nagłówki są w innej wersji (w przypadku nagłówków adresowania) lub zostały przetworzone w ramach Komunikacja między klientem a routerem.

Określa, czy nagłówek jest umieszczony w wiadomości wychodzącej, czy jest oznaczony jako zrozumiały dla warstwy kanału przychodzącego. Nagłówki, które nie są zrozumiałe (takie jak nagłówki niestandardowe), nie są usuwane i dlatego są przekazywane przez usługę routingu przez kopiowaną do wiadomości wychodzącej. Treść wiadomości jest kopiowana do wiadomości wychodzącej. Komunikat jest następnie wysyłany do kanału wychodzącego, w którym wskazuje, że wszystkie nagłówki i inne dane koperty specyficzne dla tego protokołu komunikacyjnego/transportu zostaną utworzone i dodane.

Takie kroki przetwarzania są wykonywane, gdy zostanie określone zachowanie przetwarzania protokołu SOAP. [ To\<soapProcessingExtension >](soapprocessing.md) jest zachowaniem punktu końcowego, który jest stosowany do wszystkich punktów końcowych klienta (wychodzących) podczas uruchamiania usługi routingu. Domyślnie zachowanie `processMessages` > [ routingutworzyidołączanowezachowaniesoapProcessingExtension>zustawieniemdlakażdegopunktukońcowegoklienta.\<](routing-of-servicebehavior.md) [ \<](soapprocessing.md) `true` Jeśli masz protokół, którego usługa routingu nie rozpoznaje, lub chcesz zastąpić domyślne zachowanie podczas przetwarzania, możesz wyłączyć przetwarzanie protokołu SOAP dla całej usługi routingu lub tylko dla określonych punktów końcowych.  Aby wyłączyć przetwarzanie protokołu SOAP dla całej usługi routingu we wszystkich punktach końcowych `soapProcessing` , ustaw atrybut [ \<zachowania > routingu](routing-of-servicebehavior.md) na `false`. Aby wyłączyć przetwarzanie protokołu SOAP dla określonego punktu końcowego, użyj tego zachowania i ustaw jego `processMessages` atrybut na `false`, a następnie Dołącz to zachowanie do punktu końcowego, którego domyślny kod przetwarzania nie ma być uruchamiany.  Gdy zachowanie [> routingupowodujeskonfigurowanieusługiroutingu,spowodujetopominięcieponownegozastosowaniazachowaniapunktukońcowegoodmomentu,gdyjużistnieje.\<](routing-of-servicebehavior.md)
