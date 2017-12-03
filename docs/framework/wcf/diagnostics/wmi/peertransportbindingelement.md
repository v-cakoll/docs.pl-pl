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
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="7800c-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7800c-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="7800c-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7800c-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7800c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7800c-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7800c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7800c-105">Methods</span></span>  
 <span data-ttu-id="7800c-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7800c-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7800c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7800c-107">Properties</span></span>  
 <span data-ttu-id="7800c-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7800c-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="7800c-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="7800c-109">ListenIPAddress</span></span>  
 <span data-ttu-id="7800c-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7800c-110">Data type: string</span></span>  
  
 <span data-ttu-id="7800c-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7800c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7800c-112">Adres IP, na którym węzeł elementu równorzędnego nasłuchuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7800c-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="7800c-113">Port</span><span class="sxs-lookup"><span data-stu-id="7800c-113">Port</span></span>  
 <span data-ttu-id="7800c-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7800c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="7800c-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7800c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7800c-116">Port interfejsu sieciowego, na którym znajduje się ten procesów powiązania elementu równorzędnego kanału wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7800c-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="7800c-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="7800c-117">Security</span></span>  
 <span data-ttu-id="7800c-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7800c-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="7800c-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7800c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7800c-120">Ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="7800c-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7800c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7800c-121">Requirements</span></span>  
  
|<span data-ttu-id="7800c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7800c-122">MOF</span></span>|<span data-ttu-id="7800c-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7800c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7800c-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7800c-124">Namespace</span></span>|<span data-ttu-id="7800c-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7800c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7800c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7800c-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
