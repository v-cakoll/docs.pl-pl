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
ms.openlocfilehash: e9b9bc8e364342a601c0738d5a64c5eac3cb7e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447713"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="b2be6-102">IMetaDataImport::EnumTypeSpecs — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2be6-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="b2be6-103">Wylicza tokenów elementu TypeSpec zdefiniowany w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2be6-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2be6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2be6-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2be6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2be6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2be6-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b2be6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b2be6-107">Ta wartość musi być równa NULL, pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="b2be6-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="b2be6-108">[out] Tablica używany do przechowywania tokenów elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b2be6-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2be6-109">[in] Maksymalny rozmiar `rTypeSpecs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b2be6-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="b2be6-110">[out] Liczba tokenów elementu TypeSpec zwracane w `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="b2be6-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2be6-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2be6-111">Return Value</span></span>  
  
|<span data-ttu-id="b2be6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2be6-112">HRESULT</span></span>|<span data-ttu-id="b2be6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b2be6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2be6-114">`EnumTypeSpecs` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b2be6-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2be6-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b2be6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b2be6-116">W takim przypadku `pcTypeSpecs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="b2be6-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2be6-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2be6-117">Remarks</span></span>  
 <span data-ttu-id="b2be6-118">Element TypeSpec tokenów są tworzone przez [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b2be6-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2be6-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2be6-119">Requirements</span></span>  
 <span data-ttu-id="b2be6-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2be6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2be6-121">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2be6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2be6-122">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2be6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2be6-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2be6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2be6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2be6-124">See Also</span></span>  
 [<span data-ttu-id="b2be6-125">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2be6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b2be6-126">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2be6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
