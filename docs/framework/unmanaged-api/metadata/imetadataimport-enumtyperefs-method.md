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
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175437"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="bce54-102">IMetaDataImport::EnumTypeRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="bce54-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="bce54-103">Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="bce54-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bce54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bce54-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bce54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bce54-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bce54-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="bce54-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bce54-107">Musi to być null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="bce54-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="bce54-108">[na zewnątrz] Tablica używana do przechowywania tokenów TypeRef.</span><span class="sxs-lookup"><span data-stu-id="bce54-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bce54-109">[w] Maksymalny rozmiar `rTypeRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="bce54-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="bce54-110">[na zewnątrz] Wskaźnik do liczby tokenów TypeRef `rTypeRefs`zwróconych w .</span><span class="sxs-lookup"><span data-stu-id="bce54-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bce54-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bce54-111">Return Value</span></span>  
  
|<span data-ttu-id="bce54-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bce54-112">HRESULT</span></span>|<span data-ttu-id="bce54-113">Opis</span><span class="sxs-lookup"><span data-stu-id="bce54-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bce54-114">`EnumTypeRefs`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="bce54-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bce54-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bce54-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bce54-116">W takim `pcTypeRefs` przypadku wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="bce54-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bce54-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bce54-117">Remarks</span></span>  
 <span data-ttu-id="bce54-118">Token TypeRef reprezentuje odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="bce54-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bce54-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bce54-119">Requirements</span></span>  
 <span data-ttu-id="bce54-120">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bce54-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bce54-121">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="bce54-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bce54-122">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bce54-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bce54-123">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bce54-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce54-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bce54-124">See also</span></span>

- [<span data-ttu-id="bce54-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bce54-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bce54-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bce54-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
