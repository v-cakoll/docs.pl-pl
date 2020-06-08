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
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503747"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="85d87-102">IMetaDataImport::EnumTypeRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="85d87-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="85d87-103">Wylicza tokeny TypeRef zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="85d87-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85d87-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85d87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85d87-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="85d87-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="85d87-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="85d87-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="85d87-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="85d87-108">określoną Tablica służąca do przechowywania tokenów elementu TypeRef.</span><span class="sxs-lookup"><span data-stu-id="85d87-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="85d87-109">podczas Maksymalny rozmiar `rTypeRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="85d87-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="85d87-110">określoną Wskaźnik do liczby tokenów TypeRef zwróconych w `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="85d87-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85d87-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85d87-111">Return Value</span></span>  
  
|<span data-ttu-id="85d87-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85d87-112">HRESULT</span></span>|<span data-ttu-id="85d87-113">Opis</span><span class="sxs-lookup"><span data-stu-id="85d87-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="85d87-114">`EnumTypeRefs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="85d87-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="85d87-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="85d87-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="85d87-116">W takim przypadku `pcTypeRefs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="85d87-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85d87-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85d87-117">Remarks</span></span>  
 <span data-ttu-id="85d87-118">Token TypeRef reprezentuje odwołanie do typu.</span><span class="sxs-lookup"><span data-stu-id="85d87-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85d87-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85d87-119">Requirements</span></span>  
 <span data-ttu-id="85d87-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85d87-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85d87-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="85d87-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85d87-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="85d87-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85d87-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85d87-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85d87-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85d87-124">See also</span></span>

- [<span data-ttu-id="85d87-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="85d87-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="85d87-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="85d87-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
