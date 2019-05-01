---
title: IMetaDataAssemblyImport::EnumManifestResources — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7abcb7b69d0f0f2c53cd236c9b4092a94e0f421c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044699"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="8a54f-102">IMetaDataAssemblyImport::EnumManifestResources — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a54f-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="8a54f-103">Pobiera wskaźnik do modułu wyliczającego dla zasobów, do którego odwołuje się do bieżącego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="8a54f-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a54f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a54f-104">Syntax</span></span>  
  
```  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="8a54f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a54f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8a54f-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8a54f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8a54f-107">Musi to być wartość null wartość przy `EnumManifestResources` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8a54f-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="8a54f-108">[out] Tablica do przechowywania `mdManifestResource` tokeny metadanych.</span><span class="sxs-lookup"><span data-stu-id="8a54f-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8a54f-109">[in] Maksymalna liczba `mdManifestResource` tokenów, które można umieścić w `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="8a54f-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8a54f-110">[out] Liczba `mdManifestResource` tokenów faktycznie umieszczone w `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="8a54f-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a54f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8a54f-111">Return Value</span></span>  
  
|<span data-ttu-id="8a54f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a54f-112">HRESULT</span></span>|<span data-ttu-id="8a54f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8a54f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8a54f-114">`EnumManifestResources` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8a54f-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8a54f-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8a54f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8a54f-116">W tym przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="8a54f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a54f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a54f-117">Requirements</span></span>  
 <span data-ttu-id="8a54f-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a54f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a54f-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8a54f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a54f-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a54f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a54f-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a54f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a54f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a54f-122">See also</span></span>

- [<span data-ttu-id="8a54f-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a54f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
