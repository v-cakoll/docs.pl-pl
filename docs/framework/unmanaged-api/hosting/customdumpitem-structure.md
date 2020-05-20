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
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616440"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="62824-102">CustomDumpItem — Struktura</span><span class="sxs-lookup"><span data-stu-id="62824-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="62824-103">Opisuje element, który ma zostać dodany do niestandardowego zrzutu w raporcie o błędach.</span><span class="sxs-lookup"><span data-stu-id="62824-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62824-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62824-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="62824-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="62824-105">Members</span></span>  
  
|<span data-ttu-id="62824-106">Członek</span><span class="sxs-lookup"><span data-stu-id="62824-106">Member</span></span>|<span data-ttu-id="62824-107">Opis</span><span class="sxs-lookup"><span data-stu-id="62824-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="62824-108">Wartość [ECustomDumpItemKind —](ecustomdumpitemkind-enumeration.md) , która wskazuje rodzaj elementu, który ma zostać dodany.</span><span class="sxs-lookup"><span data-stu-id="62824-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="62824-109">Obecnie nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="62824-109">Not currently used.</span></span> <span data-ttu-id="62824-110">Wszelkie elementy dodawane do Unii nie mogą być większe niż rozmiar wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="62824-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="62824-111">Jeśli `struct` jest wymagany, należy przydzielić go oddzielnie i wskazać.</span><span class="sxs-lookup"><span data-stu-id="62824-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62824-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62824-112">Remarks</span></span>  
 <span data-ttu-id="62824-113">[ICLRErrorReportingManager:: BeginCustomDump —](iclrerrorreportingmanager-begincustomdump-method.md) przyjmuje parametr typu `CustomDumpItem` .</span><span class="sxs-lookup"><span data-stu-id="62824-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62824-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62824-114">Requirements</span></span>  
 <span data-ttu-id="62824-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62824-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62824-116">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="62824-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="62824-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62824-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62824-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62824-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62824-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62824-119">See also</span></span>

- [<span data-ttu-id="62824-120">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="62824-120">Hosting Structures</span></span>](hosting-structures.md)
