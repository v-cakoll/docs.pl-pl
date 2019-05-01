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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 193abe173b259ff2679642e229fce96151e37872
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992306"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="af63e-102">IMetaDataImport::EnumSignatures — Metoda</span><span class="sxs-lookup"><span data-stu-id="af63e-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="af63e-103">Wylicza tokenów sygnatur reprezentujący autonomicznej podpisów w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="af63e-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af63e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af63e-104">Syntax</span></span>  
  
```  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af63e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af63e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="af63e-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="af63e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="af63e-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="af63e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="af63e-108">[out] Tablica do przechowywania tokenów sygnatur.</span><span class="sxs-lookup"><span data-stu-id="af63e-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="af63e-109">[in] Maksymalny rozmiar `rSignatures` tablicy.</span><span class="sxs-lookup"><span data-stu-id="af63e-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="af63e-110">[out] Liczba tokenów sygnatur zwracane w `rSignatures`.</span><span class="sxs-lookup"><span data-stu-id="af63e-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af63e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="af63e-111">Return Value</span></span>  
  
|<span data-ttu-id="af63e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af63e-112">HRESULT</span></span>|<span data-ttu-id="af63e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="af63e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="af63e-114">`EnumSignatures` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="af63e-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="af63e-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="af63e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="af63e-116">W takim przypadku `pcSignatures` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="af63e-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af63e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af63e-117">Remarks</span></span>  
 <span data-ttu-id="af63e-118">Tokeny sygnatury są tworzone przez [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="af63e-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af63e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af63e-119">Requirements</span></span>  
 <span data-ttu-id="af63e-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af63e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af63e-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="af63e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af63e-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af63e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af63e-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af63e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af63e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af63e-124">See also</span></span>

- [<span data-ttu-id="af63e-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="af63e-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="af63e-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="af63e-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
