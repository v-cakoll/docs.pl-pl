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
ms.openlocfilehash: 652ebf1be6a58e08da27aaed5b2e84a8f2aee98a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503773"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="432e1-102">IMetaDataImport::EnumSignatures — Metoda</span><span class="sxs-lookup"><span data-stu-id="432e1-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="432e1-103">Wylicza tokeny podpisu reprezentujące podpisy autonomiczne w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="432e1-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="432e1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="432e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="432e1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="432e1-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="432e1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="432e1-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="432e1-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="432e1-108">określoną Tablica służąca do przechowywania tokenów sygnatur.</span><span class="sxs-lookup"><span data-stu-id="432e1-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="432e1-109">podczas Maksymalny rozmiar `rSignatures` tablicy.</span><span class="sxs-lookup"><span data-stu-id="432e1-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="432e1-110">określoną Liczba tokenów sygnatury zwróconych w `rSignatures` .</span><span class="sxs-lookup"><span data-stu-id="432e1-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="432e1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="432e1-111">Return Value</span></span>  
  
|<span data-ttu-id="432e1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="432e1-112">HRESULT</span></span>|<span data-ttu-id="432e1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="432e1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="432e1-114">`EnumSignatures`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="432e1-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="432e1-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="432e1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="432e1-116">W takim przypadku `pcSignatures` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="432e1-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="432e1-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="432e1-117">Remarks</span></span>  
 <span data-ttu-id="432e1-118">Tokeny podpisu są tworzone przez metodę [IMetaDataEmit:: GetTokenFromSig —](imetadataemit-gettokenfromsig-method.md) .</span><span class="sxs-lookup"><span data-stu-id="432e1-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="432e1-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="432e1-119">Requirements</span></span>  
 <span data-ttu-id="432e1-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="432e1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="432e1-121">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="432e1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="432e1-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="432e1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="432e1-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="432e1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432e1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="432e1-124">See also</span></span>

- [<span data-ttu-id="432e1-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="432e1-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="432e1-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="432e1-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
