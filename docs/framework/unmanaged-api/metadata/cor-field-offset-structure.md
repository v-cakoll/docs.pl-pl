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
ms.openlocfilehash: 8cc803e3cf1442d324bf2eed0a37d0d236acd86d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493061"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="96b47-102">COR_FIELD_OFFSET — Struktura</span><span class="sxs-lookup"><span data-stu-id="96b47-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="96b47-103">Zapisuje przesunięcie w obrębie klasy w określonym polu.</span><span class="sxs-lookup"><span data-stu-id="96b47-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b47-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96b47-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="96b47-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="96b47-105">Members</span></span>  
  
|<span data-ttu-id="96b47-106">Członek</span><span class="sxs-lookup"><span data-stu-id="96b47-106">Member</span></span>|<span data-ttu-id="96b47-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96b47-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="96b47-108">`mdFieldDef`Token metadanych reprezentujący pole.</span><span class="sxs-lookup"><span data-stu-id="96b47-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="96b47-109">Przesunięcie pola w swojej klasie.</span><span class="sxs-lookup"><span data-stu-id="96b47-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b47-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96b47-110">Remarks</span></span>  
 <span data-ttu-id="96b47-111">[IMetaDataImport:: GetClassLayout —](imetadataimport-getclasslayout-method.md) i [IMetaDataEmit:: SetClassLayout —](imetadataemit-setclasslayout-method.md) Metoda przyjmuje parametr typu `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="96b47-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96b47-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96b47-112">Requirements</span></span>  
 <span data-ttu-id="96b47-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b47-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b47-114">**Nagłówek:** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="96b47-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="96b47-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b47-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b47-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96b47-116">See also</span></span>

- [<span data-ttu-id="96b47-117">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="96b47-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="96b47-118">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96b47-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="96b47-119">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96b47-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
