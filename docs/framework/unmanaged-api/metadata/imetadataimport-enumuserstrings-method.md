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
ms.openlocfilehash: 2a82456c8bc53e7828e447de3bab79388aa102cd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493742"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="37fef-102">IMetaDataImport::EnumUserStrings — Metoda</span><span class="sxs-lookup"><span data-stu-id="37fef-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="37fef-103">Wylicza tokenów ciąg reprezentujący zakodowane sprzętowo ciągi w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="37fef-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37fef-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37fef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37fef-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="37fef-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="37fef-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="37fef-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="37fef-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="37fef-108">[out] Tablica do przechowywania tokenów ciąg.</span><span class="sxs-lookup"><span data-stu-id="37fef-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="37fef-109">[in] Maksymalny rozmiar `rStrings` tablicy.</span><span class="sxs-lookup"><span data-stu-id="37fef-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="37fef-110">[out] Liczba tokenów ciąg zwracany w `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="37fef-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37fef-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37fef-111">Return Value</span></span>  
  
|<span data-ttu-id="37fef-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37fef-112">HRESULT</span></span>|<span data-ttu-id="37fef-113">Opis</span><span class="sxs-lookup"><span data-stu-id="37fef-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="37fef-114">`EnumUserStrings` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="37fef-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="37fef-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="37fef-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="37fef-116">W takim przypadku `pcStrings` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="37fef-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37fef-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37fef-117">Remarks</span></span>  
 <span data-ttu-id="37fef-118">Tokeny ciągu są tworzone przez [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="37fef-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="37fef-119">Ta metoda jest przeznaczona do użycia przez przeglądarkę metadanych, a nie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="37fef-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fef-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37fef-120">Requirements</span></span>  
 <span data-ttu-id="37fef-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fef-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fef-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="37fef-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37fef-123">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37fef-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37fef-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fef-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fef-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37fef-125">See also</span></span>
- [<span data-ttu-id="37fef-126">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="37fef-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="37fef-127">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="37fef-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
