---
title: CorRefToDefCheck — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450120"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="3adad-102">CorRefToDefCheck — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3adad-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="3adad-103">Określa flagi do kontrolowania, które elementy, do których istnieją odwołania, są konwertowane na ich definicje, aby zoptymalizować kod.</span><span class="sxs-lookup"><span data-stu-id="3adad-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3adad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3adad-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="3adad-105">Members</span><span class="sxs-lookup"><span data-stu-id="3adad-105">Members</span></span>  
  
|<span data-ttu-id="3adad-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3adad-106">Member</span></span>|<span data-ttu-id="3adad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3adad-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="3adad-108">Określa, że odwołania do typu i odwołania do elementów członkowskich powinny być konwertowane na definicje.</span><span class="sxs-lookup"><span data-stu-id="3adad-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="3adad-109">Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="3adad-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="3adad-110">Określa, że wszystkie elementy, do których istnieją odwołania, powinny być konwertowane na definicje.</span><span class="sxs-lookup"><span data-stu-id="3adad-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="3adad-111">Określa, że żadne elementy, do których istnieją odwołania, nie powinny być konwertowane na definicje.</span><span class="sxs-lookup"><span data-stu-id="3adad-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="3adad-112">Określa, że odwołania do typu mają być konwertowane do definicji typu.</span><span class="sxs-lookup"><span data-stu-id="3adad-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="3adad-113">Określa, że tylko odwołania składowe powinny być konwertowane na definicje.</span><span class="sxs-lookup"><span data-stu-id="3adad-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="3adad-114">Oznacza to, że odwołania do elementów członkowskich powinny być konwertowane na definicje metod lub definicje pól.</span><span class="sxs-lookup"><span data-stu-id="3adad-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3adad-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3adad-115">Requirements</span></span>  
 <span data-ttu-id="3adad-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3adad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3adad-117">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="3adad-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3adad-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3adad-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3adad-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3adad-119">See also</span></span>

- [<span data-ttu-id="3adad-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3adad-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
