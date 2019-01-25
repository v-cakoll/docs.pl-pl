---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 5ec2ae0db7239ff0c376ab4a8f050cc4f1df4f71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683977"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="d0662-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0662-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="d0662-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0662-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0662-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0662-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="d0662-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d0662-105">Methods</span></span>  
 <span data-ttu-id="d0662-106">Klasa ConnectionOrientedTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="d0662-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0662-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d0662-107">Properties</span></span>  
 <span data-ttu-id="d0662-108">Klasa ConnectionOrientedTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d0662-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="d0662-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="d0662-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="d0662-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="d0662-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="d0662-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-112">Timespan określający czas inicjowania kanału musi ukończyć przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d0662-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="d0662-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="d0662-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="d0662-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="d0662-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d0662-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-116">Rozmiar buforu używany do przesyłania fragmentów serializacji wiadomości na łączu z klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="d0662-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="d0662-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="d0662-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="d0662-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d0662-118">Data type: string</span></span>  
  
 <span data-ttu-id="d0662-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-120">Wartość, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d0662-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="d0662-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="d0662-121">MaxBufferSize</span></span>  
 <span data-ttu-id="d0662-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="d0662-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="d0662-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-124">Maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="d0662-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="d0662-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="d0662-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="d0662-126">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="d0662-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="d0662-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-128">Maksymalny interwał czasu, który fragment wiadomości lub cały komunikat może pozostać buforowanych w pamięci przed wysłane.</span><span class="sxs-lookup"><span data-stu-id="d0662-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="d0662-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="d0662-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="d0662-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="d0662-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="d0662-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-132">Maksymalna liczba oczekujących asynchronicznych zaakceptować wątki, które są dostępne do przetwarzania przychodzących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="d0662-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="d0662-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="d0662-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="d0662-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="d0662-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="d0662-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-136">Maksymalna liczba oczekujących połączeń.</span><span class="sxs-lookup"><span data-stu-id="d0662-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="d0662-137">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="d0662-137">TransferMode</span></span>  
 <span data-ttu-id="d0662-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d0662-138">Data type: string</span></span>  
  
 <span data-ttu-id="d0662-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d0662-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0662-140">Wartość, która określa, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="d0662-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0662-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0662-141">Requirements</span></span>  
  
|<span data-ttu-id="d0662-142">MOF</span><span class="sxs-lookup"><span data-stu-id="d0662-142">MOF</span></span>|<span data-ttu-id="d0662-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0662-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0662-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="d0662-144">Namespace</span></span>|<span data-ttu-id="d0662-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0662-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0662-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0662-146">See also</span></span>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
