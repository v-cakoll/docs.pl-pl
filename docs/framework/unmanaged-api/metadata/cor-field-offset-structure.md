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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c4a5c8efc87940b7df0bfd532beaa67931a8c81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="a2e85-102">COR_FIELD_OFFSET — Struktura</span><span class="sxs-lookup"><span data-stu-id="a2e85-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="a2e85-103">Przechowuje przesunięcie, w obrębie klasy, określonego pola.</span><span class="sxs-lookup"><span data-stu-id="a2e85-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2e85-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="a2e85-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a2e85-105">Members</span></span>  
  
|<span data-ttu-id="a2e85-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a2e85-106">Member</span></span>|<span data-ttu-id="a2e85-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2e85-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="a2e85-108">`mdFieldDef` Token metadanych, który reprezentuje pole.</span><span class="sxs-lookup"><span data-stu-id="a2e85-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="a2e85-109">Przesunięcie pole w klasie.</span><span class="sxs-lookup"><span data-stu-id="a2e85-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e85-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2e85-110">Remarks</span></span>  
 <span data-ttu-id="a2e85-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) i [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody przyjmują parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="a2e85-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e85-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2e85-112">Requirements</span></span>  
 <span data-ttu-id="a2e85-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e85-114">**Nagłówek:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a2e85-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="a2e85-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e85-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e85-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2e85-116">See Also</span></span>  
 [<span data-ttu-id="a2e85-117">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="a2e85-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="a2e85-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2e85-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a2e85-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2e85-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
