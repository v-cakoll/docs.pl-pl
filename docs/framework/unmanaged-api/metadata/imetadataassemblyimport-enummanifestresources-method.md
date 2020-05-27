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
ms.openlocfilehash: 560a6adf85fab7f421b86cba52224d5b1bfe1089
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006262"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="e779f-102">IMetaDataAssemblyImport::EnumManifestResources — Metoda</span><span class="sxs-lookup"><span data-stu-id="e779f-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="e779f-103">Pobiera wskaźnik do modułu wyliczającego dla zasobów, do których odwołuje się bieżący manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="e779f-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e779f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e779f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e779f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e779f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e779f-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="e779f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e779f-107">Ta wartość musi być wartością null, gdy `EnumManifestResources` Metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e779f-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="e779f-108">określoną Tablica służąca do przechowywania `mdManifestResource` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="e779f-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e779f-109">podczas Maksymalna liczba `mdManifestResource` tokenów, które mogą być umieszczone w `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="e779f-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e779f-110">określoną Liczba `mdManifestResource` tokenów, które zostały umieszczone w rzeczywistości `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="e779f-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e779f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e779f-111">Return Value</span></span>  
  
|<span data-ttu-id="e779f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e779f-112">HRESULT</span></span>|<span data-ttu-id="e779f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e779f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e779f-114">`EnumManifestResources`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="e779f-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e779f-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e779f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e779f-116">W tym przypadku `pcTokens` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="e779f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e779f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e779f-117">Requirements</span></span>  
 <span data-ttu-id="e779f-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e779f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e779f-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e779f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e779f-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e779f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e779f-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e779f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e779f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e779f-122">See also</span></span>

- [<span data-ttu-id="e779f-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e779f-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
