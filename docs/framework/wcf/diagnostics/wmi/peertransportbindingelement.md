---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="290ce-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="290ce-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="290ce-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="290ce-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="290ce-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="290ce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="290ce-105">Methods</span></span>  
 <span data-ttu-id="290ce-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="290ce-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="290ce-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="290ce-107">Properties</span></span>  
 <span data-ttu-id="290ce-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="290ce-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="290ce-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="290ce-109">ListenIPAddress</span></span>  
 <span data-ttu-id="290ce-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="290ce-110">Data type: string</span></span>  
  
 <span data-ttu-id="290ce-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="290ce-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="290ce-112">Adres IP, na którym węzeł elementu równorzędnego nasłuchuje wiadomości.</span><span class="sxs-lookup"><span data-stu-id="290ce-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="290ce-113">Port</span><span class="sxs-lookup"><span data-stu-id="290ce-113">Port</span></span>  
 <span data-ttu-id="290ce-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="290ce-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="290ce-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="290ce-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="290ce-116">Port interfejsu sieciowego, na którym znajduje się ten procesów powiązania elementu równorzędnego kanału wiadomości.</span><span class="sxs-lookup"><span data-stu-id="290ce-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="290ce-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="290ce-117">Security</span></span>  
 <span data-ttu-id="290ce-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="290ce-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="290ce-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="290ce-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="290ce-120">Ustawienia zabezpieczeń transportu elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="290ce-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="290ce-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="290ce-121">Requirements</span></span>  
  
|<span data-ttu-id="290ce-122">MOF</span><span class="sxs-lookup"><span data-stu-id="290ce-122">MOF</span></span>|<span data-ttu-id="290ce-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="290ce-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="290ce-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="290ce-124">Namespace</span></span>|<span data-ttu-id="290ce-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="290ce-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="290ce-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="290ce-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
