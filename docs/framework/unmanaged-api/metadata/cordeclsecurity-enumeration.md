---
title: CorDeclSecurity — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136971"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="86b66-102">CorDeclSecurity — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="86b66-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="86b66-103">Określa akcje zabezpieczeń, które mogą być wykonywane przy użyciu zabezpieczeń deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="86b66-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86b66-104">Syntax</span></span>  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="86b66-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="86b66-105">Members</span></span>  
  
|<span data-ttu-id="86b66-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="86b66-106">Member</span></span>|<span data-ttu-id="86b66-107">Opis</span><span class="sxs-lookup"><span data-stu-id="86b66-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="86b66-108">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="86b66-109">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="86b66-110">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="86b66-111">Wszystkie podmioty wywołujące wyżej w stosie wywołań są wymagane do udzielono uprawnienia określone przez bieżący obiekt uprawnień.</span><span class="sxs-lookup"><span data-stu-id="86b66-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="86b66-112">Kod wywołujący może uzyskać dostępu do zasobu, identyfikowane przez bieżący obiekt uprawnienia, nawet wtedy, gdy wyżej w stosie wywołań nie przyznano uprawnień dostępu do zasobu</span><span class="sxs-lookup"><span data-stu-id="86b66-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="86b66-113">Możliwość dostępu do zasobu, określony przez bieżący obiekt uprawnień nie jest możliwy obiektów wywołujących, nawet wtedy, gdy przyznano im uprawnienia dostępu do niego.</span><span class="sxs-lookup"><span data-stu-id="86b66-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="86b66-114">Tylko zasoby, które zostały określone przez ten obiekt uprawnień są dostępne, nawet jeśli kod ma uprawnienia dostępu do innych zasobów.</span><span class="sxs-lookup"><span data-stu-id="86b66-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="86b66-115">Do bezpośredniego wywołującego jest wymagana do przyznano określone uprawnienie dla danego okresu czasu.</span><span class="sxs-lookup"><span data-stu-id="86b66-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="86b66-116">Klasa pochodna dziedziczy innej klasy lub zastępowania metody jest wymagany do przyznano określone uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="86b66-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="86b66-117">Obiekt wywołujący może żądać minimalne uprawnienia wymagane do kod wymagany do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="86b66-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="86b66-118">Tej akcji należy używać tylko w ramach zakresu zestawu.</span><span class="sxs-lookup"><span data-stu-id="86b66-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="86b66-119">Obiekt wywołujący może żądać uzyskać dodatkowe uprawnienia, które są opcjonalne (nie wymaga do uruchomienia).</span><span class="sxs-lookup"><span data-stu-id="86b66-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="86b66-120">To żądanie niejawnie odmawia innych uprawnień nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="86b66-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="86b66-121">Tej akcji należy używać tylko w ramach zakresu zestawu.</span><span class="sxs-lookup"><span data-stu-id="86b66-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="86b66-122">Żądanie obiektu wywołującego uprawnienia, które mogą być używane nie zostaną przyznane.</span><span class="sxs-lookup"><span data-stu-id="86b66-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="86b66-123">Tej akcji należy używać tylko w ramach zakresu zestawu.</span><span class="sxs-lookup"><span data-stu-id="86b66-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="86b66-124">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="86b66-125">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="86b66-126">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="86b66-127">Bezpośredniego obiektu wywołującego jest wymagana do przyznano określone uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="86b66-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="86b66-128">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="86b66-129">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="86b66-130">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="86b66-131">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="86b66-132">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="86b66-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86b66-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86b66-133">Requirements</span></span>  
 <span data-ttu-id="86b66-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86b66-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b66-135">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="86b66-135">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="86b66-136">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="86b66-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86b66-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86b66-137">See also</span></span>

- [<span data-ttu-id="86b66-138">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="86b66-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
