---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 761ed0e30c6acca8c910c5dc97dfbae46c1f89bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564841"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="ecaaf-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ecaaf-102">PeerSecuritySettings</span></span>
<span data-ttu-id="ecaaf-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ecaaf-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecaaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecaaf-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ecaaf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ecaaf-105">Methods</span></span>  
 <span data-ttu-id="ecaaf-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ecaaf-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ecaaf-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ecaaf-107">Properties</span></span>  
 <span data-ttu-id="ecaaf-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ecaaf-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="ecaaf-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="ecaaf-109">Mode</span></span>  
 <span data-ttu-id="ecaaf-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ecaaf-110">Data type: string</span></span>  
  
 <span data-ttu-id="ecaaf-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ecaaf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecaaf-112">Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="ecaaf-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="ecaaf-113">Transport</span><span class="sxs-lookup"><span data-stu-id="ecaaf-113">Transport</span></span>  
 <span data-ttu-id="ecaaf-114">Typ danych: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ecaaf-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="ecaaf-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ecaaf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecaaf-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="ecaaf-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecaaf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecaaf-117">Requirements</span></span>  
  
|<span data-ttu-id="ecaaf-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ecaaf-118">MOF</span></span>|<span data-ttu-id="ecaaf-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ecaaf-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ecaaf-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ecaaf-120">Namespace</span></span>|<span data-ttu-id="ecaaf-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ecaaf-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecaaf-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecaaf-122">See also</span></span>
- <xref:System.ServiceModel.PeerSecuritySettings>
