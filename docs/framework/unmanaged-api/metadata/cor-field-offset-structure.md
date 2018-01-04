---
title: "COR_FIELD_OFFSET — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD_OFFSET
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_FIELD_OFFSET
helpviewer_keywords: COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed41538ae4c1e70843c613493eee9d632dff5f91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="650af-102">COR_FIELD_OFFSET — Struktura</span><span class="sxs-lookup"><span data-stu-id="650af-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="650af-103">Przechowuje przesunięcie, w obrębie klasy, określonego pola.</span><span class="sxs-lookup"><span data-stu-id="650af-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="650af-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="650af-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="650af-105">Members</span></span>  
  
|<span data-ttu-id="650af-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="650af-106">Member</span></span>|<span data-ttu-id="650af-107">Opis</span><span class="sxs-lookup"><span data-stu-id="650af-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="650af-108">`mdFieldDef` Token metadanych, który reprezentuje pole.</span><span class="sxs-lookup"><span data-stu-id="650af-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="650af-109">Przesunięcie pole w klasie.</span><span class="sxs-lookup"><span data-stu-id="650af-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="650af-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="650af-110">Remarks</span></span>  
 <span data-ttu-id="650af-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) i [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody przyjmują parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="650af-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650af-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="650af-112">Requirements</span></span>  
 <span data-ttu-id="650af-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650af-114">**Nagłówek:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="650af-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="650af-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650af-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="650af-116">See Also</span></span>  
 [<span data-ttu-id="650af-117">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="650af-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="650af-118">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="650af-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="650af-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="650af-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
