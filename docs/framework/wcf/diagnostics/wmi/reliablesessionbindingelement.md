---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f4aff60c96db5071d41a3f011019b05746f0c96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="1be76-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="1be76-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="1be76-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="1be76-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1be76-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1be76-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="1be76-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1be76-105">Methods</span></span>  
 <span data-ttu-id="1be76-106">Klasa obiektu ReliableSessionBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1be76-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1be76-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1be76-107">Properties</span></span>  
 <span data-ttu-id="1be76-108">Klasa obiektu ReliableSessionBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1be76-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="1be76-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="1be76-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="1be76-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="1be76-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="1be76-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-112">Interwał czasu oczekiwania przed wysłaniem potwierdzenia do źródła komunikatu za pośrednictwem niezawodnych kanałów tworzonych przez fabrykę miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="1be76-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="1be76-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="1be76-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="1be76-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1be76-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="1be76-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-116">Wartość logiczna określająca, czy włączone jest sterowanie przepływem.</span><span class="sxs-lookup"><span data-stu-id="1be76-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="1be76-117">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="1be76-117">InactivityTimeout</span></span>  
 <span data-ttu-id="1be76-118">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="1be76-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="1be76-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-120">Określa maksymalny czas, który będzie kanał zezwoli innemu uczestnikowi komunikacji nie na niewysyłanie komunikatów przed spowodowaniem błędu kanału.</span><span class="sxs-lookup"><span data-stu-id="1be76-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="1be76-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="1be76-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="1be76-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1be76-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="1be76-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-124">Maksymalna liczba kanałów oczekujących na akceptację na odbiornika.</span><span class="sxs-lookup"><span data-stu-id="1be76-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="1be76-125">Wartość MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="1be76-125">MaxRetryCount</span></span>  
 <span data-ttu-id="1be76-126">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1be76-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="1be76-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-128">Maksymalną liczbę prób niezawodny kanał ponownego przesłania wiadomości nie otrzymano potwierdzenia, poprzez wywoływanie metody `Send` kanału źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1be76-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="1be76-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="1be76-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="1be76-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1be76-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="1be76-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-132">Maksymalny rozmiar okna transmisji dla sesji niezawodnej.</span><span class="sxs-lookup"><span data-stu-id="1be76-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="1be76-133">uporządkowane</span><span class="sxs-lookup"><span data-stu-id="1be76-133">Ordered</span></span>  
 <span data-ttu-id="1be76-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1be76-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="1be76-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-136">Wartość logiczna określająca, czy komunikaty dotrą do celu w kolejności wysłania.</span><span class="sxs-lookup"><span data-stu-id="1be76-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="1be76-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="1be76-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="1be76-138">Typ danych: liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="1be76-138">Data type: integer</span></span>  
  
 <span data-ttu-id="1be76-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1be76-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1be76-140">Liczba całkowita określająca wersja protokołu WS-ReliableMessaging, używanego w niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="1be76-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be76-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1be76-141">Requirements</span></span>  
  
|<span data-ttu-id="1be76-142">MOF</span><span class="sxs-lookup"><span data-stu-id="1be76-142">MOF</span></span>|<span data-ttu-id="1be76-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1be76-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1be76-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1be76-144">Namespace</span></span>|<span data-ttu-id="1be76-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1be76-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1be76-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1be76-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
