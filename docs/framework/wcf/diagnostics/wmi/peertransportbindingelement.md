---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185186"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="10be2-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="10be2-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="10be2-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="10be2-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10be2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10be2-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="10be2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="10be2-105">Methods</span></span>  
 <span data-ttu-id="10be2-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="10be2-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="10be2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="10be2-107">Properties</span></span>  
 <span data-ttu-id="10be2-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="10be2-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="10be2-109">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="10be2-109">ListenIPAddress</span></span>  
 <span data-ttu-id="10be2-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="10be2-110">Data type: string</span></span>  
  
 <span data-ttu-id="10be2-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10be2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10be2-112">Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="10be2-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="10be2-113">Port</span><span class="sxs-lookup"><span data-stu-id="10be2-113">Port</span></span>  
 <span data-ttu-id="10be2-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="10be2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="10be2-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10be2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10be2-116">Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.</span><span class="sxs-lookup"><span data-stu-id="10be2-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="10be2-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="10be2-117">Security</span></span>  
 <span data-ttu-id="10be2-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="10be2-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="10be2-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="10be2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="10be2-120">Ustawienia zabezpieczeń transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="10be2-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10be2-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10be2-121">Requirements</span></span>  
  
|<span data-ttu-id="10be2-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="10be2-122">MOF</span></span>|<span data-ttu-id="10be2-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="10be2-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="10be2-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="10be2-124">Namespace</span></span>|<span data-ttu-id="10be2-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="10be2-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10be2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10be2-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
