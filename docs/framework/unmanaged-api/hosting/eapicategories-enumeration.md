---
title: EApiCategories — Wyliczenie
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25348410387a7b0e03ef897e8534336baeb126a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="54c5e-102">EApiCategories — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="54c5e-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="54c5e-103">Opis kategorii możliwości, które host może zablokować uruchamianie w częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54c5e-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="54c5e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54c5e-105">Members</span></span>  
  
|<span data-ttu-id="54c5e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="54c5e-106">Member</span></span>|<span data-ttu-id="54c5e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="54c5e-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="54c5e-108">Określa wszystkie zarządzane klasy i elementów członkowskich, które są objęte przez inne `EApiCategories` pola zablokowane w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="54c5e-109">Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, modyfikowanie i zniszczenie procesów zewnętrznych zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="54c5e-110">Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="54c5e-111">Określa, że typy zarządzane i elementów członkowskich, które potencjalnie może wyciek pamięci na przerwania zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="54c5e-112">Określa, że zablokowany żadnych kategorii kodu zarządzanego w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="54c5e-113">Określa, że zablokowany wspólną infrastrukturę zabezpieczeń dla języka wspólnego (CLR) używanych przez kod częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="54c5e-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="54c5e-114">Określa, że zarządzanych klas i członków, których możliwości mogą mieć wpływ na proces hostowanej zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="54c5e-115">Określa, że zarządzanych klas i członków, których możliwości mogą mieć wpływ na wątki w procesie hostowanej zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="54c5e-116">Określa, że zarządzanych klas i elementów członkowskich, które udostępniają stan współużytkowany zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="54c5e-117">Określa, że typowe klasy środowiska uruchomieniowego języka i elementy członkowskie, które kodu użytkownika pomieścić blokad zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="54c5e-118">Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają lub wymaga interakcji zablokowany w programie częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="54c5e-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c5e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54c5e-119">Remarks</span></span>  
 <span data-ttu-id="54c5e-120">[ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda przyjmuje parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="54c5e-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="54c5e-121">`EApiCategories` Wyliczenie i `SetProtectedCategories` metody odnoszą się bezpośrednio do zarządzanego <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="54c5e-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="54c5e-122">Zarządzanej klasy jest używany z <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> wyliczenia, których wartości odpowiada bezpośrednio do `EApiCategories` wartości, aby oznaczyć typy zarządzane i elementów członkowskich, które ujawnia możliwości odpowiadający kategorii opisanego przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="54c5e-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c5e-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54c5e-123">Requirements</span></span>  
 <span data-ttu-id="54c5e-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c5e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c5e-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54c5e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54c5e-126">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54c5e-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54c5e-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c5e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c5e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54c5e-128">See Also</span></span>  
 [<span data-ttu-id="54c5e-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="54c5e-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="54c5e-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="54c5e-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
