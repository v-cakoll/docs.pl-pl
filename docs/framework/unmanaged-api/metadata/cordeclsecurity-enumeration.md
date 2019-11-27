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
ms.openlocfilehash: 98183ed02f8821b7c40852de2d040775d30f2518
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443741"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="8aabf-102">CorDeclSecurity — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8aabf-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="8aabf-103">Określa akcje zabezpieczeń, które mogą być wykonywane przy użyciu zabezpieczeń deklaratywnych.</span><span class="sxs-lookup"><span data-stu-id="8aabf-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aabf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8aabf-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="8aabf-105">Members</span><span class="sxs-lookup"><span data-stu-id="8aabf-105">Members</span></span>  
  
|<span data-ttu-id="8aabf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8aabf-106">Member</span></span>|<span data-ttu-id="8aabf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8aabf-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="8aabf-108">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="8aabf-109">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="8aabf-110">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="8aabf-111">Wszystkie obiekty wywołujące wyższe w stosie wywołań muszą mieć przyznane uprawnienia określone przez bieżący obiekt uprawnień.</span><span class="sxs-lookup"><span data-stu-id="8aabf-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="8aabf-112">Kod wywołujący może uzyskać dostęp do zasobu identyfikowanego przez bieżący obiekt uprawnień, nawet jeśli obiekty wywołujące wyższe w stosie nie uzyskały uprawnień dostępu do zasobu</span><span class="sxs-lookup"><span data-stu-id="8aabf-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="8aabf-113">Możliwość dostępu do zasobu określonego przez bieżący obiekt uprawnień jest odrzucana dla wywołujących, nawet jeśli udzielono uprawnień dostępu do niej.</span><span class="sxs-lookup"><span data-stu-id="8aabf-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="8aabf-114">Dostęp do zasobów określonych przez ten obiekt uprawnień można uzyskać nawet wtedy, gdy do kodu udzielono uprawnień dostępu do innych zasobów.</span><span class="sxs-lookup"><span data-stu-id="8aabf-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="8aabf-115">Bezpośredni obiekt wywołujący musi mieć przyznane określone uprawnienie w danym okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="8aabf-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="8aabf-116">Klasa pochodna dziedziczenia innej klasy lub przesłaniania metody jest wymagana do przyznania określonego uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="8aabf-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="8aabf-117">Obiekt wywołujący może żądać minimalnych uprawnień wymaganych do uruchomienia kodu.</span><span class="sxs-lookup"><span data-stu-id="8aabf-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="8aabf-118">Tej akcji można używać tylko w zakresie zestawu.</span><span class="sxs-lookup"><span data-stu-id="8aabf-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="8aabf-119">Obiekt wywołujący może żądać dodatkowych uprawnień, które są opcjonalne (niewymagane do uruchomienia).</span><span class="sxs-lookup"><span data-stu-id="8aabf-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="8aabf-120">To żądanie niejawnie odrzuca wszystkie inne uprawnienia, które nie zostały zażądane.</span><span class="sxs-lookup"><span data-stu-id="8aabf-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="8aabf-121">Tej akcji można używać tylko w zakresie zestawu.</span><span class="sxs-lookup"><span data-stu-id="8aabf-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="8aabf-122">Żądanie obiektu wywołującego dla uprawnień, które mogą być nieużywane, nie zostanie przyznane.</span><span class="sxs-lookup"><span data-stu-id="8aabf-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="8aabf-123">Tej akcji można używać tylko w zakresie zestawu.</span><span class="sxs-lookup"><span data-stu-id="8aabf-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="8aabf-124">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="8aabf-125">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="8aabf-126">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="8aabf-127">Bezpośredni obiekt wywołujący musi mieć przyznane określone uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="8aabf-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="8aabf-128">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="8aabf-129">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="8aabf-130">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="8aabf-131">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="8aabf-132">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8aabf-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8aabf-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8aabf-133">Requirements</span></span>  
 <span data-ttu-id="8aabf-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aabf-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aabf-135">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8aabf-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8aabf-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aabf-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aabf-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aabf-137">See also</span></span>

- [<span data-ttu-id="8aabf-138">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8aabf-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
