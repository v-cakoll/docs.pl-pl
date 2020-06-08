---
title: IMetaDataImport::EnumTypeSpecs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503721"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="c7a66-102">IMetaDataImport::EnumTypeSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="c7a66-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="c7a66-103">Wylicza tokeny elementu TypeSpec zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="c7a66-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7a66-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7a66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7a66-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c7a66-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c7a66-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c7a66-107">Ta wartość musi być RÓWNa NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="c7a66-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="c7a66-108">określoną Tablica służąca do przechowywania tokenów elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="c7a66-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c7a66-109">podczas Maksymalny rozmiar `rTypeSpecs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c7a66-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="c7a66-110">określoną Liczba zwróconych tokenów elementu TypeSpec w `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="c7a66-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7a66-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c7a66-111">Return Value</span></span>  
  
|<span data-ttu-id="c7a66-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7a66-112">HRESULT</span></span>|<span data-ttu-id="c7a66-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c7a66-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c7a66-114">`EnumTypeSpecs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="c7a66-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c7a66-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c7a66-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c7a66-116">W takim przypadku `pcTypeSpecs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="c7a66-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7a66-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7a66-117">Remarks</span></span>  
 <span data-ttu-id="c7a66-118">Tokeny elementu TypeSpec są tworzone przez metodę [IMetaDataEmit:: GetTokenFromTypeSpec —](imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c7a66-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a66-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c7a66-119">Requirements</span></span>  
 <span data-ttu-id="c7a66-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a66-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a66-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7a66-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7a66-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c7a66-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7a66-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a66-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a66-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7a66-124">See also</span></span>

- [<span data-ttu-id="c7a66-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c7a66-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c7a66-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c7a66-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
