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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="347c9-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="347c9-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="347c9-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="347c9-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="347c9-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="347c9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="347c9-105">Methods</span></span>  
 <span data-ttu-id="347c9-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="347c9-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="347c9-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="347c9-107">Properties</span></span>  
 <span data-ttu-id="347c9-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="347c9-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="347c9-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="347c9-109">ListenIPAddress</span></span>  
 <span data-ttu-id="347c9-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="347c9-110">Data type: string</span></span>  
  
 <span data-ttu-id="347c9-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="347c9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="347c9-112">Adres IP, na którym węzeł elementu równorzędnego nasłuchuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="347c9-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="347c9-113">Port</span><span class="sxs-lookup"><span data-stu-id="347c9-113">Port</span></span>  
 <span data-ttu-id="347c9-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="347c9-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="347c9-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="347c9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="347c9-116">Port interfejsu sieciowego, na którym znajduje się ten procesów powiązania elementu równorzędnego kanału wiadomości.</span><span class="sxs-lookup"><span data-stu-id="347c9-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="347c9-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="347c9-117">Security</span></span>  
 <span data-ttu-id="347c9-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="347c9-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="347c9-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="347c9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="347c9-120">Ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="347c9-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="347c9-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="347c9-121">Requirements</span></span>  
  
|<span data-ttu-id="347c9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="347c9-122">MOF</span></span>|<span data-ttu-id="347c9-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="347c9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="347c9-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="347c9-124">Namespace</span></span>|<span data-ttu-id="347c9-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="347c9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="347c9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="347c9-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
