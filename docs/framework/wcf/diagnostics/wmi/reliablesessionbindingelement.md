---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962919"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="212a2-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="212a2-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="212a2-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="212a2-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="212a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="212a2-104">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="212a2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="212a2-105">Methods</span></span>  
 <span data-ttu-id="212a2-106">Klasa elementu ReliableSessionBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="212a2-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="212a2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="212a2-107">Properties</span></span>  
 <span data-ttu-id="212a2-108">Klasa elementu ReliableSessionBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="212a2-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="212a2-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="212a2-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="212a2-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="212a2-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="212a2-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-112">Interwał czasu miejsca docelowego oczekiwania przed wysłaniem potwierdzenia do źródła wiadomości na niezawodne kanały, które są tworzone przez fabrykę.</span><span class="sxs-lookup"><span data-stu-id="212a2-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="212a2-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="212a2-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="212a2-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="212a2-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="212a2-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-116">Wartość logiczna określająca, czy włączone jest sterowanie przepływem.</span><span class="sxs-lookup"><span data-stu-id="212a2-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="212a2-117">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="212a2-117">InactivityTimeout</span></span>  
 <span data-ttu-id="212a2-118">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="212a2-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="212a2-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-120">Określa maksymalny czas, przez który kanał umożliwi drugiej strony komunikujące się nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.</span><span class="sxs-lookup"><span data-stu-id="212a2-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="212a2-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="212a2-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="212a2-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="212a2-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="212a2-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-124">Maksymalną liczbę kanałów oczekujących na odbiornik do zaakceptowania.</span><span class="sxs-lookup"><span data-stu-id="212a2-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="212a2-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="212a2-125">MaxRetryCount</span></span>  
 <span data-ttu-id="212a2-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="212a2-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="212a2-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-128">Maksymalną liczbę prób niezawodny kanał retransmitować komunikat, którego nie otrzymano potwierdzenia, wywołując `Send` kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="212a2-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="212a2-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="212a2-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="212a2-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="212a2-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="212a2-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-132">Rozmiar okna maksymalną niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="212a2-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="212a2-133">Uporządkowane</span><span class="sxs-lookup"><span data-stu-id="212a2-133">Ordered</span></span>  
 <span data-ttu-id="212a2-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="212a2-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="212a2-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-136">Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="212a2-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="212a2-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="212a2-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="212a2-138">Typ danych: liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="212a2-138">Data type: integer</span></span>  
  
 <span data-ttu-id="212a2-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="212a2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="212a2-140">Liczba całkowita, która określa wersję protokołu WS-ReliableMessaging, które są używane w niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="212a2-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="212a2-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="212a2-141">Requirements</span></span>  
  
|<span data-ttu-id="212a2-142">MOF</span><span class="sxs-lookup"><span data-stu-id="212a2-142">MOF</span></span>|<span data-ttu-id="212a2-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="212a2-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="212a2-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="212a2-144">Namespace</span></span>|<span data-ttu-id="212a2-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="212a2-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="212a2-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="212a2-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
