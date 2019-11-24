---
title: COR_FIELD_OFFSET — Struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443965"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="06976-102">COR_FIELD_OFFSET — Struktura</span><span class="sxs-lookup"><span data-stu-id="06976-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="06976-103">Stores the offset, within a class, of the specified field.</span><span class="sxs-lookup"><span data-stu-id="06976-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06976-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06976-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="06976-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="06976-105">Members</span></span>  
  
|<span data-ttu-id="06976-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06976-106">Member</span></span>|<span data-ttu-id="06976-107">Opis</span><span class="sxs-lookup"><span data-stu-id="06976-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="06976-108">An `mdFieldDef` metadata token that represents the field.</span><span class="sxs-lookup"><span data-stu-id="06976-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="06976-109">The field's offset within its class.</span><span class="sxs-lookup"><span data-stu-id="06976-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06976-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06976-110">Remarks</span></span>  
 <span data-ttu-id="06976-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="06976-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06976-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06976-112">Requirements</span></span>  
 <span data-ttu-id="06976-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06976-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06976-114">**Header:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="06976-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="06976-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06976-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06976-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06976-116">See also</span></span>

- [<span data-ttu-id="06976-117">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="06976-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="06976-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="06976-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="06976-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="06976-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
