---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2e2e36486c3788cd714ffd0ed545fbb14f831476
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50038896"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="00f69-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="00f69-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="00f69-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="00f69-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00f69-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="00f69-105">Metody</span><span class="sxs-lookup"><span data-stu-id="00f69-105">Methods</span></span>  
 <span data-ttu-id="00f69-106">Klasa elementu ReliableSessionBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="00f69-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="00f69-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="00f69-107">Properties</span></span>  
 <span data-ttu-id="00f69-108">Klasa elementu ReliableSessionBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="00f69-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="00f69-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="00f69-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="00f69-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="00f69-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="00f69-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-112">Interwał czasu miejsca docelowego oczekiwania przed wysłaniem potwierdzenia do źródła wiadomości na niezawodne kanały, które są tworzone przez fabrykę.</span><span class="sxs-lookup"><span data-stu-id="00f69-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="00f69-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="00f69-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="00f69-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="00f69-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="00f69-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-116">Wartość logiczna określająca, czy włączone jest sterowanie przepływem.</span><span class="sxs-lookup"><span data-stu-id="00f69-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="00f69-117">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="00f69-117">InactivityTimeout</span></span>  
 <span data-ttu-id="00f69-118">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="00f69-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="00f69-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-120">Określa maksymalny czas, przez który kanał umożliwi drugiej strony komunikujące się nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.</span><span class="sxs-lookup"><span data-stu-id="00f69-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="00f69-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="00f69-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="00f69-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="00f69-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="00f69-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-124">Maksymalną liczbę kanałów oczekujących na odbiornik do zaakceptowania.</span><span class="sxs-lookup"><span data-stu-id="00f69-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="00f69-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="00f69-125">MaxRetryCount</span></span>  
 <span data-ttu-id="00f69-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="00f69-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="00f69-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-128">Maksymalną liczbę prób niezawodny kanał retransmitować komunikat, którego nie otrzymano potwierdzenia, wywołując `Send` kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="00f69-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="00f69-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="00f69-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="00f69-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="00f69-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="00f69-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-132">Rozmiar okna maksymalną niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="00f69-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="00f69-133">Uporządkowane</span><span class="sxs-lookup"><span data-stu-id="00f69-133">Ordered</span></span>  
 <span data-ttu-id="00f69-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="00f69-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="00f69-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-136">Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="00f69-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="00f69-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="00f69-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="00f69-138">Typ danych: liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="00f69-138">Data type: integer</span></span>  
  
 <span data-ttu-id="00f69-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="00f69-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="00f69-140">Liczba całkowita, która określa wersję protokołu WS-ReliableMessaging, które są używane w niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="00f69-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f69-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00f69-141">Requirements</span></span>  
  
|<span data-ttu-id="00f69-142">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="00f69-142">MOF</span></span>|<span data-ttu-id="00f69-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="00f69-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="00f69-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="00f69-144">Namespace</span></span>|<span data-ttu-id="00f69-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="00f69-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="00f69-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00f69-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
