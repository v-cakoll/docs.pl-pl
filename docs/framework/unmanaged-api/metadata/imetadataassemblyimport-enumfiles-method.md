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
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177815"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="78f5d-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="78f5d-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="78f5d-103">Wylicza pliki, do których odwołuje się bieżący manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="78f5d-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78f5d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78f5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78f5d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="78f5d-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="78f5d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="78f5d-107">Musi to być wartość null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="78f5d-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="78f5d-108">[na zewnątrz] Tablica używana do `mdFile` przechowywania tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="78f5d-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="78f5d-109">[w] Maksymalna liczba `mdFile` tokenów, które `rFiles`można umieścić w .</span><span class="sxs-lookup"><span data-stu-id="78f5d-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="78f5d-110">[na zewnątrz] Liczba tokenów `mdFile` faktycznie umieszczonych w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="78f5d-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f5d-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78f5d-111">Return Value</span></span>  
  
|<span data-ttu-id="78f5d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78f5d-112">HRESULT</span></span>|<span data-ttu-id="78f5d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="78f5d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="78f5d-114">`EnumFiles`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="78f5d-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="78f5d-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="78f5d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="78f5d-116">W takim `pcTokens` przypadku jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="78f5d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78f5d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78f5d-117">Requirements</span></span>  
 <span data-ttu-id="78f5d-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f5d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f5d-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="78f5d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78f5d-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78f5d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78f5d-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f5d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f5d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78f5d-122">See also</span></span>

- [<span data-ttu-id="78f5d-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="78f5d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
