---
title: IMetaDataImport::EnumSignatures — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 9dbbdcc9d0fb9f0a8d2a64edfa4a0ad92570933c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450008"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="1fe35-102">IMetaDataImport::EnumSignatures — Metoda</span><span class="sxs-lookup"><span data-stu-id="1fe35-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="1fe35-103">Wylicza tokeny podpisu reprezentujące podpisy autonomiczne w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1fe35-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fe35-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fe35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fe35-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1fe35-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1fe35-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1fe35-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="1fe35-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="1fe35-108">określoną Tablica służąca do przechowywania tokenów sygnatur.</span><span class="sxs-lookup"><span data-stu-id="1fe35-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1fe35-109">podczas Maksymalny rozmiar tablicy `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="1fe35-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="1fe35-110">określoną Liczba tokenów sygnatury zwróconych w `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="1fe35-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fe35-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1fe35-111">Return Value</span></span>  
  
|<span data-ttu-id="1fe35-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1fe35-112">HRESULT</span></span>|<span data-ttu-id="1fe35-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1fe35-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1fe35-114">`EnumSignatures` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="1fe35-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1fe35-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1fe35-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1fe35-116">W takim przypadku `pcSignatures` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1fe35-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fe35-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fe35-117">Remarks</span></span>  
 <span data-ttu-id="1fe35-118">Tokeny podpisu są tworzone przez metodę [IMetaDataEmit:: GetTokenFromSig —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1fe35-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe35-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1fe35-119">Requirements</span></span>  
 <span data-ttu-id="1fe35-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fe35-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe35-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1fe35-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fe35-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1fe35-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1fe35-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe35-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe35-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fe35-124">See also</span></span>

- [<span data-ttu-id="1fe35-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe35-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1fe35-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1fe35-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
