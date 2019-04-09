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
ms.openlocfilehash: 820c99de1bdb108a24203a3438b1709ca54490b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078125"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="63f3a-102">COR_FIELD_OFFSET — Struktura</span><span class="sxs-lookup"><span data-stu-id="63f3a-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="63f3a-103">Przechowuje przesunięcie, w obrębie klasy, określonego pola.</span><span class="sxs-lookup"><span data-stu-id="63f3a-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63f3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63f3a-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="63f3a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="63f3a-105">Members</span></span>  
  
|<span data-ttu-id="63f3a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="63f3a-106">Member</span></span>|<span data-ttu-id="63f3a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="63f3a-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="63f3a-108">`mdFieldDef` Token metadanych, który reprezentuje pole.</span><span class="sxs-lookup"><span data-stu-id="63f3a-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="63f3a-109">Pole Przesunięcie w swojej klasie.</span><span class="sxs-lookup"><span data-stu-id="63f3a-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63f3a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63f3a-110">Remarks</span></span>  
 <span data-ttu-id="63f3a-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) i [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody przyjmują parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="63f3a-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f3a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63f3a-112">Requirements</span></span>  
 <span data-ttu-id="63f3a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f3a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f3a-114">**Nagłówek:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="63f3a-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 **<span data-ttu-id="63f3a-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="63f3a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63f3a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63f3a-116">See also</span></span>

- [<span data-ttu-id="63f3a-117">Metadane — Struktury</span><span class="sxs-lookup"><span data-stu-id="63f3a-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="63f3a-118">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63f3a-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="63f3a-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63f3a-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
