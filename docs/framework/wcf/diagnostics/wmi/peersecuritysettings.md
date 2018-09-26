---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: c74ee82d7aa3a23f0ee6a69185ad45857c31bb0b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087882"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="da61e-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="da61e-102">PeerSecuritySettings</span></span>
<span data-ttu-id="da61e-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="da61e-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da61e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da61e-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="da61e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="da61e-105">Methods</span></span>  
 <span data-ttu-id="da61e-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="da61e-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="da61e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="da61e-107">Properties</span></span>  
 <span data-ttu-id="da61e-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="da61e-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="da61e-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="da61e-109">Mode</span></span>  
 <span data-ttu-id="da61e-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="da61e-110">Data type: string</span></span>  
  
 <span data-ttu-id="da61e-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="da61e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da61e-112">Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="da61e-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="da61e-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="da61e-113">Transport</span></span>  
 <span data-ttu-id="da61e-114">Typ danych: Obiekt PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="da61e-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="da61e-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="da61e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da61e-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="da61e-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da61e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da61e-117">Requirements</span></span>  
  
|<span data-ttu-id="da61e-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="da61e-118">MOF</span></span>|<span data-ttu-id="da61e-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="da61e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="da61e-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="da61e-120">Namespace</span></span>|<span data-ttu-id="da61e-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="da61e-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da61e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da61e-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
