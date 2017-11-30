---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e53225399e3acba275d2d95533c4baad20386a4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="9345e-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="9345e-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="9345e-103">Określa zachowanie punktu końcowego klienta używany do organizowania wiadomości między inne powiązanie typy i wersje komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9345e-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="9345e-104">**\<System. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="9345e-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="9345e-105">&nbsp;&nbsp;**\<zachowania >** </span><span class="sxs-lookup"><span data-stu-id="9345e-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="9345e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="9345e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="9345e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<zachowanie >** </span><span class="sxs-lookup"><span data-stu-id="9345e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="9345e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="9345e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9345e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9345e-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9345e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9345e-110">Attributes and elements</span></span>

<span data-ttu-id="9345e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9345e-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9345e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9345e-112">Attributes</span></span>

|                   | <span data-ttu-id="9345e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9345e-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="9345e-114">Wartość logiczna określająca, czy wiadomości powinny być przekazywane między wersjami wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="9345e-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9345e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9345e-115">Child elements</span></span>

<span data-ttu-id="9345e-116">Brak</span><span class="sxs-lookup"><span data-stu-id="9345e-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9345e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9345e-117">Parent elements</span></span>

|     | <span data-ttu-id="9345e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9345e-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9345e-119">**\<zachowanie >**</span><span class="sxs-lookup"><span data-stu-id="9345e-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="9345e-120">Określa zachowanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9345e-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9345e-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9345e-121">Remarks</span></span>

<span data-ttu-id="9345e-122">Przetwarzania protokołu SOAP to proces, w których wiadomości są konwertowane między wersjami wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9345e-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="9345e-123">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Usługa routingu można przekonwertować wiadomości z jednego protokołu na inny.</span><span class="sxs-lookup"><span data-stu-id="9345e-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="9345e-124">Jeśli wersje komunikatów przychodzących i wychodzących są różne, tworzona jest nowa wiadomość o poprawnej wersji.</span><span class="sxs-lookup"><span data-stu-id="9345e-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="9345e-125">Przetwarzanie komunikatów z jednym <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` do innego odbywa się przez utworzenie nowej [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikat, który zawiera część treści i odpowiednie nagłówków z przychodzącego [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9345e-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="9345e-126">Nagłówki specyficznych dla adresowania lub które są zrozumiałe na poziomie routera, nie są używane podczas tworzenia nowej wiadomości WCF, ponieważ te nagłówki są albo inną wersję (w przypadku adresowania nagłówki) lub są przetwarzane w ramach Komunikacja między klientem a router.</span><span class="sxs-lookup"><span data-stu-id="9345e-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="9345e-127">Określa, czy nagłówek jest umieszczany w wiadomości wychodzącej jest określana przez czy została oznaczona jako rozumieć przeszła przychodzące warstwie kanału.</span><span class="sxs-lookup"><span data-stu-id="9345e-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="9345e-128">Nagłówki, które nie są zrozumiałe (np. nagłówki niestandardowe) nie są usuwane i dlatego Przekaż za pośrednictwem usługi routingu przez kopiowane do wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="9345e-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="9345e-129">Treść wiadomości jest kopiowany do wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="9345e-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="9345e-130">Komunikat jest następnie wysyłane kanału wychodzącego, w tym momencie wszystkie nagłówki oraz innych danych koperty określonych na komunikat zostanie utworzona i dodać protokół/transport.</span><span class="sxs-lookup"><span data-stu-id="9345e-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="9345e-131">Takie kroki przetwarzania ma miejsce, gdy określono zachowania przetwarzania protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9345e-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="9345e-132">To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowanie jest zachowanie punktu końcowego, który jest stosowany do wszystkich punktów końcowych klienta (wychodzące), podczas uruchamiania usługi routingu.</span><span class="sxs-lookup"><span data-stu-id="9345e-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="9345e-133">Domyślnie [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie tworzy i dołącza nowy [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowanie w przypadku `processMessages` ustawioną `true` dla każdego punkt końcowy klienta.</span><span class="sxs-lookup"><span data-stu-id="9345e-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="9345e-134">Jeśli protokół usługi routingu nie zrozumieć lub chcesz zastąpić domyślne zachowanie przetwarzania, można wyłączyć przetwarzania dla całej usługi routingu lub tylko dla konkretnego punktów końcowych protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9345e-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="9345e-135">Aby wyłączyć przetwarzania dla całej usługi routingu dla wszystkich punktów końcowych SOAP, ustaw `soapProcessing` atrybutu [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowania `false`.</span><span class="sxs-lookup"><span data-stu-id="9345e-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="9345e-136">Aby wyłączyć SOAP przetwarzania dla danego punktu końcowego, należy użyć tego zachowania i ustawić jej `processMessages` atrybutu `false`, następnie dołączyć tego zachowania do punktu końcowego nie ma domyślnego przetwarzania kodu w.</span><span class="sxs-lookup"><span data-stu-id="9345e-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="9345e-137">Gdy [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie konfiguruje usługi routingu, pominie ponowne zastosowanie zachowania punktu końcowego, ponieważ już istnieje.</span><span class="sxs-lookup"><span data-stu-id="9345e-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
