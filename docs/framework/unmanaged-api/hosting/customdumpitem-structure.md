---
title: CustomDumpItem — Struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f742d219d603488bbade091f7a8192785d3e84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433099"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="6474e-102">CustomDumpItem — Struktura</span><span class="sxs-lookup"><span data-stu-id="6474e-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="6474e-103">Opis elementu do dodania do niestandardowych zrzutu w raportowaniu błędów.</span><span class="sxs-lookup"><span data-stu-id="6474e-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6474e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6474e-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="6474e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6474e-105">Members</span></span>  
  
|<span data-ttu-id="6474e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6474e-106">Member</span></span>|<span data-ttu-id="6474e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6474e-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="6474e-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) wartość, która wskazuje rodzaj elementu do dodania.</span><span class="sxs-lookup"><span data-stu-id="6474e-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="6474e-109">Obecnie nieużywane.</span><span class="sxs-lookup"><span data-stu-id="6474e-109">Not currently used.</span></span> <span data-ttu-id="6474e-110">Wszystkie elementy dodane do Unii nie może być większe niż rozmiar wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="6474e-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="6474e-111">Jeśli `struct` jest wymagane, należy przydzielić je oddzielnie i wskaż go.</span><span class="sxs-lookup"><span data-stu-id="6474e-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6474e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6474e-112">Remarks</span></span>  
 <span data-ttu-id="6474e-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="6474e-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6474e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6474e-114">Requirements</span></span>  
 <span data-ttu-id="6474e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6474e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6474e-116">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="6474e-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6474e-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6474e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6474e-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6474e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6474e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6474e-119">See Also</span></span>  
 [<span data-ttu-id="6474e-120">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="6474e-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
