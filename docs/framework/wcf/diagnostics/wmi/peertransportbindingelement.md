---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="25708-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="25708-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="25708-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="25708-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25708-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25708-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="25708-105">Metody</span><span class="sxs-lookup"><span data-stu-id="25708-105">Methods</span></span>  
 <span data-ttu-id="25708-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="25708-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="25708-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="25708-107">Properties</span></span>  
 <span data-ttu-id="25708-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="25708-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="25708-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="25708-109">ListenIPAddress</span></span>  
 <span data-ttu-id="25708-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="25708-110">Data type: string</span></span>  
  
 <span data-ttu-id="25708-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="25708-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25708-112">Adres IP, na którym węzeł elementu równorzędnego nasłuchuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="25708-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="25708-113">Port</span><span class="sxs-lookup"><span data-stu-id="25708-113">Port</span></span>  
 <span data-ttu-id="25708-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="25708-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="25708-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="25708-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25708-116">Port interfejsu sieciowego, na którym znajduje się ten procesów powiązania elementu równorzędnego kanału wiadomości.</span><span class="sxs-lookup"><span data-stu-id="25708-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="25708-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="25708-117">Security</span></span>  
 <span data-ttu-id="25708-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="25708-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="25708-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="25708-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25708-120">Ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="25708-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25708-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25708-121">Requirements</span></span>  
  
|<span data-ttu-id="25708-122">MOF</span><span class="sxs-lookup"><span data-stu-id="25708-122">MOF</span></span>|<span data-ttu-id="25708-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="25708-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="25708-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="25708-124">Namespace</span></span>|<span data-ttu-id="25708-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="25708-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25708-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25708-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
