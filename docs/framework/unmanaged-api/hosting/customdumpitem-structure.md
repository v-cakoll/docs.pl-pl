---
title: "CustomDumpItem — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CustomDumpItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CustomDumpItem
helpviewer_keywords: CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 547204385b20d5b7e64bda9ea0a9e790f2ba3471
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="023af-102">CustomDumpItem — Struktura</span><span class="sxs-lookup"><span data-stu-id="023af-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="023af-103">Opis elementu do dodania do niestandardowych zrzutu w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="023af-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="023af-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="023af-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="023af-105">Members</span></span>  
  
|<span data-ttu-id="023af-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="023af-106">Member</span></span>|<span data-ttu-id="023af-107">Opis</span><span class="sxs-lookup"><span data-stu-id="023af-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="023af-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) wartość, która wskazuje rodzaj elementu do dodania.</span><span class="sxs-lookup"><span data-stu-id="023af-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="023af-109">Obecnie nieużywane.</span><span class="sxs-lookup"><span data-stu-id="023af-109">Not currently used.</span></span> <span data-ttu-id="023af-110">Wszystkie elementy dodane do Unii nie może być większe niż rozmiar wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="023af-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="023af-111">Jeśli `struct` jest wymagane, należy przydzielić je oddzielnie i wskaż go.</span><span class="sxs-lookup"><span data-stu-id="023af-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="023af-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="023af-112">Remarks</span></span>  
 <span data-ttu-id="023af-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="023af-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023af-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="023af-114">Requirements</span></span>  
 <span data-ttu-id="023af-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="023af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="023af-116">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="023af-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="023af-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="023af-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="023af-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="023af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023af-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="023af-119">See Also</span></span>  
 [<span data-ttu-id="023af-120">Hosting — struktury</span><span class="sxs-lookup"><span data-stu-id="023af-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
