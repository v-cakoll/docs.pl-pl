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
ms.openlocfilehash: 02cd483f2f7ec5e599b286b672d051a0e8d57940
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="090b3-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="090b3-102">PeerSecuritySettings</span></span>
<span data-ttu-id="090b3-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="090b3-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="090b3-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="090b3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="090b3-105">Methods</span></span>  
 <span data-ttu-id="090b3-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="090b3-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="090b3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="090b3-107">Properties</span></span>  
 <span data-ttu-id="090b3-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="090b3-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="090b3-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="090b3-109">Mode</span></span>  
 <span data-ttu-id="090b3-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="090b3-110">Data type: string</span></span>  
  
 <span data-ttu-id="090b3-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="090b3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="090b3-112">Określa, czy poziom komunikatu i zabezpieczenia na poziomie transportu są używane przez punkt końcowy skonfigurowany dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="090b3-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="090b3-113">Transportu</span><span class="sxs-lookup"><span data-stu-id="090b3-113">Transport</span></span>  
 <span data-ttu-id="090b3-114">Typ danych: Obiekt PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="090b3-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="090b3-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="090b3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="090b3-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="090b3-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="090b3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="090b3-117">Requirements</span></span>  
  
|<span data-ttu-id="090b3-118">MOF</span><span class="sxs-lookup"><span data-stu-id="090b3-118">MOF</span></span>|<span data-ttu-id="090b3-119">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="090b3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="090b3-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="090b3-120">Namespace</span></span>|<span data-ttu-id="090b3-121">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="090b3-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="090b3-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="090b3-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
