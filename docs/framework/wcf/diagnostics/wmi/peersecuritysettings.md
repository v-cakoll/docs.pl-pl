---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 92aca4c790607de91314aacf6414d0dfacea9a9f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193165"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="4aba4-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4aba4-102">PeerSecuritySettings</span></span>
<span data-ttu-id="4aba4-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4aba4-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aba4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4aba4-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4aba4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4aba4-105">Methods</span></span>  
 <span data-ttu-id="4aba4-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4aba4-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4aba4-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4aba4-107">Properties</span></span>  
 <span data-ttu-id="4aba4-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4aba4-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="4aba4-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="4aba4-109">Mode</span></span>  
 <span data-ttu-id="4aba4-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4aba4-110">Data type: string</span></span>  
  
 <span data-ttu-id="4aba4-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4aba4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aba4-112">Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="4aba4-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="4aba4-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="4aba4-113">Transport</span></span>  
 <span data-ttu-id="4aba4-114">Typ danych: Obiekt PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4aba4-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="4aba4-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4aba4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aba4-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="4aba4-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aba4-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4aba4-117">Requirements</span></span>  
  
|<span data-ttu-id="4aba4-118">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="4aba4-118">MOF</span></span>|<span data-ttu-id="4aba4-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4aba4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4aba4-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4aba4-120">Namespace</span></span>|<span data-ttu-id="4aba4-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4aba4-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4aba4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4aba4-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
