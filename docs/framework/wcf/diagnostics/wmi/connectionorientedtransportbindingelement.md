---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0d399eb859118dfe94eb9e0a421fa405ae0f414
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="f452b-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f452b-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="f452b-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f452b-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f452b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f452b-104">Syntax</span></span>  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f452b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f452b-105">Methods</span></span>  
 <span data-ttu-id="f452b-106">Klasa ConnectionOrientedTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f452b-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f452b-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f452b-107">Properties</span></span>  
 <span data-ttu-id="f452b-108">Klasa ConnectionOrientedTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f452b-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="f452b-109">limitu czasu channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="f452b-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="f452b-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f452b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="f452b-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-112">Obiekt timespan określający sposób inicjacji kanału musi zostać ukończona przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="f452b-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="f452b-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="f452b-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="f452b-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f452b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f452b-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-116">Rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="f452b-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="f452b-117">parametru hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f452b-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="f452b-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f452b-118">Data type: string</span></span>  
  
 <span data-ttu-id="f452b-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-120">Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f452b-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="f452b-121">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="f452b-121">MaxBufferSize</span></span>  
 <span data-ttu-id="f452b-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f452b-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="f452b-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-124">Maksymalny rozmiar bufora.</span><span class="sxs-lookup"><span data-stu-id="f452b-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="f452b-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="f452b-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="f452b-126">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f452b-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="f452b-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-128">Maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowana w pamięci przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="f452b-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="f452b-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="f452b-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="f452b-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f452b-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="f452b-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-132">Maksymalna liczba oczekujących asynchronicznych wątków dostępnych do przetwarzania przychodzących połączeń z usługą akceptujących.</span><span class="sxs-lookup"><span data-stu-id="f452b-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="f452b-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="f452b-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="f452b-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f452b-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="f452b-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-136">Maksymalna liczba oczekujących połączeń.</span><span class="sxs-lookup"><span data-stu-id="f452b-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="f452b-137">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="f452b-137">TransferMode</span></span>  
 <span data-ttu-id="f452b-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f452b-138">Data type: string</span></span>  
  
 <span data-ttu-id="f452b-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f452b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f452b-140">Wartość, która określa, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="f452b-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f452b-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f452b-141">Requirements</span></span>  
  
|<span data-ttu-id="f452b-142">MOF</span><span class="sxs-lookup"><span data-stu-id="f452b-142">MOF</span></span>|<span data-ttu-id="f452b-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f452b-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f452b-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f452b-144">Namespace</span></span>|<span data-ttu-id="f452b-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f452b-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f452b-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f452b-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
