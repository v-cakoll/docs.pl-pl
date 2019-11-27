---
title: IMetaDataAssemblyImport::EnumFiles — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: e4549789ea1af584c0850a535d9f6bb54f844ce0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443545"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="5cdf2-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="5cdf2-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="5cdf2-103">Wylicza pliki, do których odwołuje się bieżący manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cdf2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cdf2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cdf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cdf2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5cdf2-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5cdf2-107">Musi to być wartość null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="5cdf2-108">określoną Tablica służąca do przechowywania tokenów metadanych `mdFile`.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5cdf2-109">podczas Maksymalna liczba tokenów `mdFile`, które można umieścić w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5cdf2-110">określoną Liczba tokenów `mdFile` faktycznie umieszczonych w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cdf2-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5cdf2-111">Return Value</span></span>  
  
|<span data-ttu-id="5cdf2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cdf2-112">HRESULT</span></span>|<span data-ttu-id="5cdf2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5cdf2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5cdf2-114">`EnumFiles` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5cdf2-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5cdf2-116">W tym przypadku `pcTokens` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="5cdf2-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cdf2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cdf2-117">Requirements</span></span>  
 <span data-ttu-id="5cdf2-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cdf2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cdf2-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5cdf2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cdf2-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5cdf2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cdf2-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cdf2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdf2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cdf2-122">See also</span></span>

- [<span data-ttu-id="5cdf2-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="5cdf2-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
