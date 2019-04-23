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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4be12e46851b11a5e6db60c351094a356fa61f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082948"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="5f425-102">IMetaDataImport::EnumUserStrings — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f425-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="5f425-103">Wylicza tokenów ciąg reprezentujący zakodowane sprzętowo ciągi w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="5f425-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f425-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f425-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f425-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f425-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5f425-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5f425-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5f425-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="5f425-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="5f425-108">[out] Tablica do przechowywania tokenów ciąg.</span><span class="sxs-lookup"><span data-stu-id="5f425-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5f425-109">[in] Maksymalny rozmiar `rStrings` tablicy.</span><span class="sxs-lookup"><span data-stu-id="5f425-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="5f425-110">[out] Liczba tokenów ciąg zwracany w `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="5f425-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f425-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5f425-111">Return Value</span></span>  
  
|<span data-ttu-id="5f425-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f425-112">HRESULT</span></span>|<span data-ttu-id="5f425-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5f425-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5f425-114">`EnumUserStrings` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="5f425-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5f425-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5f425-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5f425-116">W takim przypadku `pcStrings` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="5f425-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f425-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f425-117">Remarks</span></span>  
 <span data-ttu-id="5f425-118">Tokeny ciągu są tworzone przez [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5f425-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="5f425-119">Ta metoda jest przeznaczona do użycia przez przeglądarkę metadanych, a nie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="5f425-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f425-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f425-120">Requirements</span></span>  
 <span data-ttu-id="5f425-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f425-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f425-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5f425-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f425-123">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f425-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f425-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f425-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f425-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f425-125">See also</span></span>

- [<span data-ttu-id="5f425-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f425-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5f425-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f425-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
