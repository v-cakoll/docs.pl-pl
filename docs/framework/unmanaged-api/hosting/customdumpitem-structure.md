---
title: "CustomDumpItem — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47fd4e1dd3889cc7eeaa37457b47d9b2fd6dd8b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="64bdd-102">CustomDumpItem — Struktura</span><span class="sxs-lookup"><span data-stu-id="64bdd-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="64bdd-103">Opis elementu do dodania do niestandardowych zrzutu w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="64bdd-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64bdd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64bdd-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="64bdd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="64bdd-105">Members</span></span>  
  
|<span data-ttu-id="64bdd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="64bdd-106">Member</span></span>|<span data-ttu-id="64bdd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="64bdd-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="64bdd-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) wartość, która wskazuje rodzaj elementu do dodania.</span><span class="sxs-lookup"><span data-stu-id="64bdd-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="64bdd-109">Obecnie nieużywane.</span><span class="sxs-lookup"><span data-stu-id="64bdd-109">Not currently used.</span></span> <span data-ttu-id="64bdd-110">Wszystkie elementy dodane do Unii nie może być większe niż rozmiar wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="64bdd-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="64bdd-111">Jeśli `struct` jest wymagane, należy przydzielić je oddzielnie i wskaż go.</span><span class="sxs-lookup"><span data-stu-id="64bdd-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64bdd-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64bdd-112">Remarks</span></span>  
 <span data-ttu-id="64bdd-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="64bdd-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64bdd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64bdd-114">Requirements</span></span>  
 <span data-ttu-id="64bdd-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64bdd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64bdd-116">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="64bdd-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="64bdd-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64bdd-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64bdd-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64bdd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64bdd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64bdd-119">See Also</span></span>  
 [<span data-ttu-id="64bdd-120">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="64bdd-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
