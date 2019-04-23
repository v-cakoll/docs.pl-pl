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
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086458"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="6ee55-102">EApiCategories — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6ee55-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="6ee55-103">Opis kategorii możliwości, które blokują hosta z systemem w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ee55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ee55-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6ee55-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6ee55-105">Members</span></span>  
  
|<span data-ttu-id="6ee55-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6ee55-106">Member</span></span>|<span data-ttu-id="6ee55-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ee55-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="6ee55-108">Określa, czy wszystkich zarządzanych klas i składowych, które są obejmowane przez inne `EApiCategories` pola zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="6ee55-109">Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenia procesy zewnętrzne zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="6ee55-110">Określa, że zarządzanych klas i elementów członkowskich, które umożliwiają tworzenie, manipulowanie i niszczenie wątków zewnętrznych zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="6ee55-111">Określa, że zarządzane typy i elementy członkowskie, które potencjalnie mogą spowodować wyciek pamięci po przerwaniu zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="6ee55-112">Określa, że nie ma kategorii kodu zarządzanego zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="6ee55-113">Określa, że zablokowany wspólnej infrastruktury języka wspólnego (CLR) zabezpieczeń używany przez częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="6ee55-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="6ee55-114">Określa, że zarządzanych klas i składowych, których możliwości mogą mieć wpływ na proces hostowanej zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="6ee55-115">Określa, że zarządzanych klas i składowych, których możliwości mogą mieć wpływ na wątki w procesie hostowanej zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="6ee55-116">Określa, że zarządzanych klas i składowych, które uwidaczniają udostępnionego stanu zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="6ee55-117">Określa, że wspólnej klasy środowiska wykonawczego języka i elementy członkowskie, które umożliwia blokady przy użyciu kodu użytkownika zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="6ee55-118">Określa, że zarządzanych klas i składowych, które blokują lub wymaga interakcji z człowiekiem zablokowany w kodzie częściowo zaufanym.</span><span class="sxs-lookup"><span data-stu-id="6ee55-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ee55-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ee55-119">Remarks</span></span>  
 <span data-ttu-id="6ee55-120">[Iclrhostprotectionmanager::setprotectedcategories —](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda przyjmuje parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="6ee55-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="6ee55-121">`EApiCategories` Wyliczenie i `SetProtectedCategories` metoda odnoszą się bezpośrednio do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="6ee55-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6ee55-122">Klasa zarządzana jest używana z <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> wyliczenia, których wartości odpowiadają bezpośrednio do `EApiCategories` wartości, aby oznaczyć zarządzane typy i elementy członkowskie, które udostępniają funkcje odpowiadającej kategorii opisanych przez `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="6ee55-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ee55-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ee55-123">Requirements</span></span>  
 <span data-ttu-id="6ee55-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ee55-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ee55-125">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ee55-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ee55-126">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ee55-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ee55-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ee55-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee55-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ee55-128">See also</span></span>

- [<span data-ttu-id="6ee55-129">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ee55-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="6ee55-130">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6ee55-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
