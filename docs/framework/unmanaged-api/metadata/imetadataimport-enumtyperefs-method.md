---
title: IMetaDataImport::EnumTypeRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de0fe4a51fbb49e80377b6b434bf3b72ddb90f02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081625"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="c28d3-102">IMetaDataImport::EnumTypeRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="c28d3-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="c28d3-103">Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="c28d3-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c28d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c28d3-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c28d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c28d3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c28d3-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c28d3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c28d3-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="c28d3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="c28d3-108">[out] Tablica do przechowywania tokenów TypeRef.</span><span class="sxs-lookup"><span data-stu-id="c28d3-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c28d3-109">[in] Maksymalny rozmiar `rTypeRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c28d3-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="c28d3-110">[out] Wskaźnik do liczby tokenów TypeRef zwracane w `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="c28d3-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c28d3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c28d3-111">Return Value</span></span>  
  
|<span data-ttu-id="c28d3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c28d3-112">HRESULT</span></span>|<span data-ttu-id="c28d3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c28d3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeRefs` <span data-ttu-id="c28d3-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="c28d3-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c28d3-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c28d3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c28d3-116">W takim przypadku `pcTypeRefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="c28d3-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c28d3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c28d3-117">Remarks</span></span>  
 <span data-ttu-id="c28d3-118">TypeRef token reprezentuje odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="c28d3-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c28d3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c28d3-119">Requirements</span></span>  
 <span data-ttu-id="c28d3-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c28d3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c28d3-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c28d3-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c28d3-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c28d3-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c28d3-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c28d3-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c28d3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c28d3-124">See also</span></span>

- [<span data-ttu-id="c28d3-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c28d3-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c28d3-126">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c28d3-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
