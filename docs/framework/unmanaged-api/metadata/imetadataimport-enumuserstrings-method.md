---
title: IMetaDataImport::EnumUserStrings — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: 1c9f15881d3515f24a63f29e9337a7a356937f2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449945"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="d1dee-102">IMetaDataImport::EnumUserStrings — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1dee-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="d1dee-103">Wylicza tokeny ciągów reprezentujące stałe ciągi w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d1dee-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1dee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1dee-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1dee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1dee-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d1dee-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="d1dee-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d1dee-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="d1dee-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="d1dee-108">określoną Tablica służąca do przechowywania tokenów ciągów.</span><span class="sxs-lookup"><span data-stu-id="d1dee-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d1dee-109">podczas Maksymalny rozmiar tablicy `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="d1dee-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="d1dee-110">określoną Liczba tokenów ciągów zwracanych w `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="d1dee-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1dee-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1dee-111">Return Value</span></span>  
  
|<span data-ttu-id="d1dee-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1dee-112">HRESULT</span></span>|<span data-ttu-id="d1dee-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d1dee-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d1dee-114">`EnumUserStrings` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d1dee-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d1dee-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d1dee-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d1dee-116">W takim przypadku `pcStrings` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="d1dee-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1dee-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1dee-117">Remarks</span></span>  
 <span data-ttu-id="d1dee-118">Tokeny ciągów są tworzone przez metodę [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d1dee-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="d1dee-119">Ta metoda jest przeznaczona do użycia przez przeglądarkę metadanych, a nie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d1dee-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1dee-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1dee-120">Requirements</span></span>  
 <span data-ttu-id="d1dee-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1dee-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1dee-122">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1dee-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1dee-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d1dee-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1dee-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1dee-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1dee-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1dee-125">See also</span></span>

- [<span data-ttu-id="d1dee-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1dee-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d1dee-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1dee-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
