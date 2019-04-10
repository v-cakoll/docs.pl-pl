---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217890"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="78a75-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="78a75-102">PeerSecuritySettings</span></span>
<span data-ttu-id="78a75-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="78a75-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78a75-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="78a75-105">Metody</span><span class="sxs-lookup"><span data-stu-id="78a75-105">Methods</span></span>  
 <span data-ttu-id="78a75-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="78a75-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="78a75-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="78a75-107">Properties</span></span>  
 <span data-ttu-id="78a75-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="78a75-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="78a75-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="78a75-109">Mode</span></span>  
 <span data-ttu-id="78a75-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="78a75-110">Data type: string</span></span>  
  
 <span data-ttu-id="78a75-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="78a75-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="78a75-112">Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="78a75-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="78a75-113">Transport</span><span class="sxs-lookup"><span data-stu-id="78a75-113">Transport</span></span>  
 <span data-ttu-id="78a75-114">Typ danych: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="78a75-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="78a75-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="78a75-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="78a75-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="78a75-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a75-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78a75-117">Requirements</span></span>  
  
|<span data-ttu-id="78a75-118">MOF</span><span class="sxs-lookup"><span data-stu-id="78a75-118">MOF</span></span>|<span data-ttu-id="78a75-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="78a75-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="78a75-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="78a75-120">Namespace</span></span>|<span data-ttu-id="78a75-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="78a75-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78a75-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78a75-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
