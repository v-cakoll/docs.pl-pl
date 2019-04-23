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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081625"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="6871f-102">IMetaDataImport::EnumTypeRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="6871f-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="6871f-103">Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="6871f-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6871f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6871f-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6871f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6871f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6871f-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="6871f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6871f-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="6871f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="6871f-108">[out] Tablica do przechowywania tokenów TypeRef.</span><span class="sxs-lookup"><span data-stu-id="6871f-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6871f-109">[in] Maksymalny rozmiar `rTypeRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6871f-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="6871f-110">[out] Wskaźnik do liczby tokenów TypeRef zwracane w `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="6871f-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6871f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6871f-111">Return Value</span></span>  
  
|<span data-ttu-id="6871f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6871f-112">HRESULT</span></span>|<span data-ttu-id="6871f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6871f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6871f-114">`EnumTypeRefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6871f-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6871f-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6871f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6871f-116">W takim przypadku `pcTypeRefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="6871f-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6871f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6871f-117">Remarks</span></span>  
 <span data-ttu-id="6871f-118">TypeRef token reprezentuje odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="6871f-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6871f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6871f-119">Requirements</span></span>  
 <span data-ttu-id="6871f-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6871f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6871f-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6871f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6871f-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6871f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6871f-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6871f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6871f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6871f-124">See also</span></span>

- [<span data-ttu-id="6871f-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6871f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6871f-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6871f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
