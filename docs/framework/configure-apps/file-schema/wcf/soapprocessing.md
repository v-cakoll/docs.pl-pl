---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399538"
---
# \<soapProcessing>

<span data-ttu-id="f60cd-101">Definiuje zachowanie punktu końcowego klienta używane do organizowania komunikatów między różnymi typami powiązań i wersjami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f60cd-101">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="f60cd-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f60cd-102">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f60cd-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f60cd-103">Attributes and elements</span></span>  
  
<span data-ttu-id="f60cd-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f60cd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f60cd-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f60cd-105">Attributes</span></span>  
  
|                   | <span data-ttu-id="f60cd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f60cd-106">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="f60cd-107">Wartość logiczna określająca, czy komunikaty powinny być organizowane między wersjami komunikatów SOAP.</span><span class="sxs-lookup"><span data-stu-id="f60cd-107">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="f60cd-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f60cd-108">Child elements</span></span>

<span data-ttu-id="f60cd-109">Brak</span><span class="sxs-lookup"><span data-stu-id="f60cd-109">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f60cd-110">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f60cd-110">Parent elements</span></span>

|     | <span data-ttu-id="f60cd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f60cd-111">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="f60cd-112">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f60cd-112">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f60cd-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f60cd-113">Remarks</span></span>

<span data-ttu-id="f60cd-114">Przetwarzanie protokołu SOAP to proces, w którym komunikaty są konwertowane między wersjami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f60cd-114">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="f60cd-115">Usługa routingu Windows Communication Foundation (WCF) umożliwia konwertowanie komunikatów z jednego protokołu na inny.</span><span class="sxs-lookup"><span data-stu-id="f60cd-115">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="f60cd-116">Jeśli wersje wiadomości przychodzących i wychodzących są różne, zostanie utworzona nowa wiadomość o prawidłowej wersji.</span><span class="sxs-lookup"><span data-stu-id="f60cd-116">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="f60cd-117">Przetwarzanie komunikatów z jednego <xref:System.ServiceModel.Channels.MessageVersion> do drugiego jest realizowane przez konstruowanie nowej wiadomości WCF zawierającej część treści i odpowiednich nagłówków z przychodzącego komunikatu WCF.</span><span class="sxs-lookup"><span data-stu-id="f60cd-117">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="f60cd-118">Nagłówki, które są specyficzne dla adresowania lub są zrozumiałe na poziomie routera, nie są używane podczas konstruowania nowej wiadomości WCF, ponieważ te nagłówki są w innej wersji (w przypadku nagłówków adresowania) lub zostały przetworzone w ramach komunikacji między klientem a routerem.</span><span class="sxs-lookup"><span data-stu-id="f60cd-118">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="f60cd-119">Określa, czy nagłówek jest umieszczony w wiadomości wychodzącej, czy jest oznaczony jako zrozumiały dla warstwy kanału przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="f60cd-119">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="f60cd-120">Nagłówki, które nie są zrozumiałe (takie jak nagłówki niestandardowe), nie są usuwane i dlatego są przekazywane przez usługę routingu przez kopiowaną do wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="f60cd-120">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="f60cd-121">Treść wiadomości jest kopiowana do wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="f60cd-121">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="f60cd-122">Komunikat jest następnie wysyłany do kanału wychodzącego, w którym wskazuje, że wszystkie nagłówki i inne dane koperty specyficzne dla tego protokołu komunikacyjnego/transportu zostaną utworzone i dodane.</span><span class="sxs-lookup"><span data-stu-id="f60cd-122">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="f60cd-123">Takie kroki przetwarzania są wykonywane, gdy zostanie określone zachowanie przetwarzania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f60cd-123">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="f60cd-124">To [\<soapProcessingExtension>](soapprocessing.md) zachowanie jest zachowaniem punktu końcowego, które jest stosowane do wszystkich punktów końcowych klienta (wychodzących) podczas uruchamiania usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="f60cd-124">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="f60cd-125">Domyślnie [\<routing>](routing-of-servicebehavior.md) zachowanie tworzy i dołącza nowe [\<soapProcessingExtension>](soapprocessing.md) zachowanie z `processMessages` ustawieniem `true` dla każdego punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f60cd-125">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="f60cd-126">Jeśli masz protokół, którego usługa routingu nie rozpoznaje, lub chcesz zastąpić domyślne zachowanie podczas przetwarzania, możesz wyłączyć przetwarzanie protokołu SOAP dla całej usługi routingu lub tylko dla określonych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="f60cd-126">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="f60cd-127">Aby wyłączyć przetwarzanie protokołu SOAP dla całej usługi routingu we wszystkich punktach końcowych, ustaw `soapProcessing` atrybut [\<routing>](routing-of-servicebehavior.md) zachowania na `false` .</span><span class="sxs-lookup"><span data-stu-id="f60cd-127">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="f60cd-128">Aby wyłączyć przetwarzanie protokołu SOAP dla określonego punktu końcowego, użyj tego zachowania i ustaw jego `processMessages` atrybut na `false` , a następnie Dołącz to zachowanie do punktu końcowego, którego domyślny kod przetwarzania nie ma być uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="f60cd-128">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="f60cd-129">Gdy [\<routing>](routing-of-servicebehavior.md) zachowanie konfiguruje usługę routingu, spowoduje to pominięcie ponownego zastosowania zachowania punktu końcowego, ponieważ już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f60cd-129">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
