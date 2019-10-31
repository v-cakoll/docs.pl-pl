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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131212"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="4c2e4-102">EApiCategories — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4c2e4-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="4c2e4-103">Opisuje kategorie możliwości, które host może blokować z uruchamiania w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c2e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c2e4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="4c2e4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4c2e4-105">Members</span></span>  
  
|<span data-ttu-id="4c2e4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4c2e4-106">Member</span></span>|<span data-ttu-id="4c2e4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4c2e4-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="4c2e4-108">Określa, że wszystkie zarządzane klasy i elementy członkowskie, które są objęte innymi polami `EApiCategories`, nie mogą być uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="4c2e4-109">Określa, że zarządzane klasy i elementy członkowskie, które umożliwiają tworzenie, manipulowanie i niszczenie procesów zewnętrznych, nie są uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="4c2e4-110">Określa, że zarządzane klasy i elementy członkowskie, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych, nie są uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="4c2e4-111">Określa, że zarządzane typy i elementy członkowskie, które mogą potencjalnie przeciekać pamięć przy przerwaniu, mogą być uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="4c2e4-112">Określa, że nie można blokować uruchamiania żadnej zarządzanej kategorii kodu w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="4c2e4-113">Określa, że infrastruktura zabezpieczeń środowiska uruchomieniowego języka wspólnego (CLR) nie może być używana przez częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="4c2e4-114">Określa, że zarządzane klasy i elementy członkowskie, których możliwości mogą mieć wpływ na proces hostowany, można zablokować z uruchamiania w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="4c2e4-115">Określa, że zarządzane klasy i elementy członkowskie, których możliwości mogą wpływać na wątki w hostowanym procesie, można zablokować uruchamiania w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="4c2e4-116">Określa, że zarządzane klasy i elementy członkowskie, które uwidaczniają stan udostępniony, nie są uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="4c2e4-117">Określa, że klasy środowiska uruchomieniowego języka wspólnego i składowe, które zezwalają na przechowywanie blokad przez kod użytkownika, nie mogą być uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="4c2e4-118">Określa, że zarządzane klasy i elementy członkowskie, które zezwalają na interakcję ludzką lub wymagają, aby nie były uruchamiane w częściowo zaufanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c2e4-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c2e4-119">Remarks</span></span>  
 <span data-ttu-id="4c2e4-120">Metoda [ICLRHostProtectionManager:: SetProtectedCategories —](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) przyjmuje parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="4c2e4-121">Wyliczenie `EApiCategories` i Metoda `SetProtectedCategories` są bezpośrednio powiązane z klasą zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4c2e4-122">Zarządzana Klasa jest używana z wyliczeniem <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, którego wartości odpowiadają bezpośrednio na wartości `EApiCategories`, aby oznaczyć typy zarządzane i składowe, które uwidaczniają możliwości odpowiadające kategoriom opisanym przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="4c2e4-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2e4-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c2e4-123">Requirements</span></span>  
 <span data-ttu-id="4c2e4-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c2e4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2e4-125">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4c2e4-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c2e4-126">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c2e4-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c2e4-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2e4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2e4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c2e4-128">See also</span></span>

- [<span data-ttu-id="4c2e4-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c2e4-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="4c2e4-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4c2e4-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
