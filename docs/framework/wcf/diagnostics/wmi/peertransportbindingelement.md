---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 437ccc0446e3cc05596ab12b7908177b7f78e431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670657"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="becea-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="becea-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="becea-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="becea-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="becea-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="becea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="becea-105">Methods</span></span>  
 <span data-ttu-id="becea-106">Klasa PeerTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="becea-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="becea-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="becea-107">Properties</span></span>  
 <span data-ttu-id="becea-108">Klasa PeerTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="becea-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="becea-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="becea-109">ListenIPAddress</span></span>  
 <span data-ttu-id="becea-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="becea-110">Data type: string</span></span>  
  
 <span data-ttu-id="becea-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="becea-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="becea-112">Adres IP, na którym węzeł równorzędny będzie nasłuchiwać pod kątem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="becea-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="becea-113">Port</span><span class="sxs-lookup"><span data-stu-id="becea-113">Port</span></span>  
 <span data-ttu-id="becea-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="becea-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="becea-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="becea-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="becea-116">Port interfejsu sieciowego, na którym znajduje się ten kanał wiadomości w komunikacji równorzędnej procesy powiązania.</span><span class="sxs-lookup"><span data-stu-id="becea-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="becea-117">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="becea-117">Security</span></span>  
 <span data-ttu-id="becea-118">Typ danych: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="becea-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="becea-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="becea-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="becea-120">Ustawienia zabezpieczeń transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="becea-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="becea-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="becea-121">Requirements</span></span>  
  
|<span data-ttu-id="becea-122">MOF</span><span class="sxs-lookup"><span data-stu-id="becea-122">MOF</span></span>|<span data-ttu-id="becea-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="becea-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="becea-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="becea-124">Namespace</span></span>|<span data-ttu-id="becea-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="becea-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="becea-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="becea-126">See also</span></span>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
