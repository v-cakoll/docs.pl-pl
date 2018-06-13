---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484524"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="e7795-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7795-102">PeerSecuritySettings</span></span>
<span data-ttu-id="e7795-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7795-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7795-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7795-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e7795-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e7795-105">Methods</span></span>  
 <span data-ttu-id="e7795-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e7795-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e7795-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e7795-107">Properties</span></span>  
 <span data-ttu-id="e7795-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e7795-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="e7795-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="e7795-109">Mode</span></span>  
 <span data-ttu-id="e7795-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e7795-110">Data type: string</span></span>  
  
 <span data-ttu-id="e7795-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e7795-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7795-112">Określa, czy poziom komunikatu i zabezpieczenia na poziomie transportu są używane przez punkt końcowy skonfigurowany dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e7795-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="e7795-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="e7795-113">Transport</span></span>  
 <span data-ttu-id="e7795-114">Typ danych: Obiekt PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e7795-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="e7795-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e7795-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7795-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="e7795-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7795-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7795-117">Requirements</span></span>  
  
|<span data-ttu-id="e7795-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e7795-118">MOF</span></span>|<span data-ttu-id="e7795-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e7795-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e7795-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e7795-120">Namespace</span></span>|<span data-ttu-id="e7795-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7795-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7795-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7795-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
