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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01151dc2fe6aa995285a34076527609816b2f3e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205163"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="3b5ab-102">IMetaDataImport::EnumTypeSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b5ab-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="3b5ab-103">Wylicza TypeSpec tokeny zdefiniowane w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b5ab-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b5ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b5ab-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3b5ab-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3b5ab-107">Ta wartość musi być wartością NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="3b5ab-108">[out] Tablica do przechowywania tokenów elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3b5ab-109">[in] Maksymalny rozmiar `rTypeSpecs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="3b5ab-110">[out] Liczba tokenów elementu TypeSpec zwracane w `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b5ab-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b5ab-111">Return Value</span></span>  
  
|<span data-ttu-id="3b5ab-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b5ab-112">HRESULT</span></span>|<span data-ttu-id="3b5ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3b5ab-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs` <span data-ttu-id="3b5ab-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3b5ab-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3b5ab-116">W takim przypadku `pcTypeSpecs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b5ab-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b5ab-117">Remarks</span></span>  
 <span data-ttu-id="3b5ab-118">Tokeny elementu TypeSpec są tworzone przez [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3b5ab-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b5ab-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b5ab-119">Requirements</span></span>  
 <span data-ttu-id="3b5ab-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b5ab-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b5ab-121">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3b5ab-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b5ab-122">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b5ab-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3b5ab-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3b5ab-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3b5ab-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b5ab-124">See also</span></span>

- [<span data-ttu-id="3b5ab-125">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3b5ab-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3b5ab-126">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3b5ab-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
