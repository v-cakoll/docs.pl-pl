---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194071"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="fef3c-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="fef3c-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="fef3c-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="fef3c-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fef3c-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fef3c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fef3c-105">Methods</span></span>  
 <span data-ttu-id="fef3c-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fef3c-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fef3c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fef3c-107">Properties</span></span>  
 <span data-ttu-id="fef3c-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fef3c-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="fef3c-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="fef3c-109">ListenIPAddress</span></span>  
 <span data-ttu-id="fef3c-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fef3c-110">Data type: string</span></span>  
  
 <span data-ttu-id="fef3c-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fef3c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fef3c-112">Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fef3c-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="fef3c-113">Port</span><span class="sxs-lookup"><span data-stu-id="fef3c-113">Port</span></span>  
 <span data-ttu-id="fef3c-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fef3c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="fef3c-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fef3c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fef3c-116">Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.</span><span class="sxs-lookup"><span data-stu-id="fef3c-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="fef3c-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="fef3c-117">Security</span></span>  
 <span data-ttu-id="fef3c-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fef3c-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="fef3c-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fef3c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fef3c-120">Ustawienia zabezpieczeń transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="fef3c-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef3c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fef3c-121">Requirements</span></span>  
  
|<span data-ttu-id="fef3c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="fef3c-122">MOF</span></span>|<span data-ttu-id="fef3c-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fef3c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fef3c-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fef3c-124">Namespace</span></span>|<span data-ttu-id="fef3c-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fef3c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fef3c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fef3c-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
