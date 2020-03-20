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
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176022"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="c36e3-102">IMetaDataAssemblyImport::EnumManifestResources — Metoda</span><span class="sxs-lookup"><span data-stu-id="c36e3-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="c36e3-103">Pobiera wskaźnik do wyliczania zasobów, do których odwołuje się w bieżącym manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="c36e3-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c36e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c36e3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c36e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c36e3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c36e3-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="c36e3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c36e3-107">Musi to być wartość `EnumManifestResources` null, gdy metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c36e3-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="c36e3-108">[na zewnątrz] Tablica używana do `mdManifestResource` przechowywania tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="c36e3-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c36e3-109">[w] Maksymalna liczba `mdManifestResource` tokenów, które `rManifestResources`można umieścić w .</span><span class="sxs-lookup"><span data-stu-id="c36e3-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c36e3-110">[na zewnątrz] Liczba tokenów `mdManifestResource` faktycznie umieszczonych w `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="c36e3-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c36e3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c36e3-111">Return Value</span></span>  
  
|<span data-ttu-id="c36e3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c36e3-112">HRESULT</span></span>|<span data-ttu-id="c36e3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c36e3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c36e3-114">`EnumManifestResources`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c36e3-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c36e3-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c36e3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c36e3-116">W takim `pcTokens` przypadku jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="c36e3-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c36e3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c36e3-117">Requirements</span></span>  
 <span data-ttu-id="c36e3-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c36e3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c36e3-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="c36e3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c36e3-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c36e3-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c36e3-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c36e3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36e3-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c36e3-122">See also</span></span>

- [<span data-ttu-id="c36e3-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c36e3-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
