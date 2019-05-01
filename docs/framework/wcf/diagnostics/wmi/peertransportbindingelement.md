---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962966"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="e201f-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e201f-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="e201f-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e201f-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e201f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e201f-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e201f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e201f-105">Methods</span></span>  
 <span data-ttu-id="e201f-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e201f-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e201f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e201f-107">Properties</span></span>  
 <span data-ttu-id="e201f-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e201f-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="e201f-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="e201f-109">ListenIPAddress</span></span>  
 <span data-ttu-id="e201f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e201f-110">Data type: string</span></span>  
  
 <span data-ttu-id="e201f-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e201f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e201f-112">Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e201f-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="e201f-113">Port</span><span class="sxs-lookup"><span data-stu-id="e201f-113">Port</span></span>  
 <span data-ttu-id="e201f-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="e201f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e201f-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e201f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e201f-116">Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.</span><span class="sxs-lookup"><span data-stu-id="e201f-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="e201f-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="e201f-117">Security</span></span>  
 <span data-ttu-id="e201f-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e201f-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="e201f-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e201f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e201f-120">Ustawienia zabezpieczeń transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="e201f-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e201f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e201f-121">Requirements</span></span>  
  
|<span data-ttu-id="e201f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e201f-122">MOF</span></span>|<span data-ttu-id="e201f-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e201f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e201f-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e201f-124">Namespace</span></span>|<span data-ttu-id="e201f-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e201f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e201f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e201f-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
