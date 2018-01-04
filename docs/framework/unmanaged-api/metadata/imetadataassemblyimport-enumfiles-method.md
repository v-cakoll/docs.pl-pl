---
title: "IMetaDataAssemblyImport::EnumFiles — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumFiles
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ce0682f6f7719c902183778578d75dd19d56867
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="61248-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="61248-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="61248-103">Wylicza pliki w bieżącym manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="61248-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61248-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61248-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61248-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61248-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="61248-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="61248-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="61248-107">Musi to być wartość null w pierwszym wywołaniu tej metody.</span><span class="sxs-lookup"><span data-stu-id="61248-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="61248-108">[out] Tablica używany do przechowywania `mdFile` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="61248-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="61248-109">[in] Maksymalna liczba `mdFile` tokenów, które można umieścić w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="61248-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="61248-110">[out] Liczba `mdFile` tokeny faktycznie umieszczone w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="61248-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61248-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61248-111">Return Value</span></span>  
  
|<span data-ttu-id="61248-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61248-112">HRESULT</span></span>|<span data-ttu-id="61248-113">Opis</span><span class="sxs-lookup"><span data-stu-id="61248-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="61248-114">`EnumFiles`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="61248-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="61248-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="61248-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="61248-116">W takim przypadku `pcTokens` jest ustawiony na zero.</span><span class="sxs-lookup"><span data-stu-id="61248-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61248-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61248-117">Requirements</span></span>  
 <span data-ttu-id="61248-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61248-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61248-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61248-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61248-120">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61248-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61248-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61248-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61248-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61248-122">See Also</span></span>  
 [<span data-ttu-id="61248-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="61248-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
