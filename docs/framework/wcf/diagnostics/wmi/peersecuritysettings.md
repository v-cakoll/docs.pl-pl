---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="e445f-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e445f-102">PeerSecuritySettings</span></span>
<span data-ttu-id="e445f-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e445f-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e445f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e445f-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e445f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e445f-105">Methods</span></span>  
 <span data-ttu-id="e445f-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e445f-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e445f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e445f-107">Properties</span></span>  
 <span data-ttu-id="e445f-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e445f-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="e445f-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="e445f-109">Mode</span></span>  
 <span data-ttu-id="e445f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e445f-110">Data type: string</span></span>  
  
 <span data-ttu-id="e445f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e445f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e445f-112">Określa, czy poziom komunikatu i zabezpieczenia na poziomie transportu są używane przez punkt końcowy skonfigurowany dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e445f-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="e445f-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="e445f-113">Transport</span></span>  
 <span data-ttu-id="e445f-114">Typ danych: Obiekt PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e445f-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="e445f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e445f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e445f-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="e445f-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e445f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e445f-117">Requirements</span></span>  
  
|<span data-ttu-id="e445f-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e445f-118">MOF</span></span>|<span data-ttu-id="e445f-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e445f-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e445f-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e445f-120">Namespace</span></span>|<span data-ttu-id="e445f-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e445f-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e445f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e445f-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
