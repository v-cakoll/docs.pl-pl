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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c402b20f9d7f0d370cfa6ec8376603efa8c3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777986"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="939e3-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="939e3-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="939e3-103">Wylicza pliki, do którego odwołuje się do bieżącego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="939e3-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="939e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="939e3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="939e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="939e3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="939e3-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="939e3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="939e3-107">Musi to być wartość null w pierwszym wywołaniu tej metody.</span><span class="sxs-lookup"><span data-stu-id="939e3-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="939e3-108">[out] Tablica do przechowywania `mdFile` tokeny metadanych.</span><span class="sxs-lookup"><span data-stu-id="939e3-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="939e3-109">[in] Maksymalna liczba `mdFile` tokenów, które można umieścić w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="939e3-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="939e3-110">[out] Liczba `mdFile` tokenów faktycznie umieszczone w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="939e3-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="939e3-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="939e3-111">Return Value</span></span>  
  
|<span data-ttu-id="939e3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="939e3-112">HRESULT</span></span>|<span data-ttu-id="939e3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="939e3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="939e3-114">`EnumFiles` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="939e3-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="939e3-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="939e3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="939e3-116">W tym przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="939e3-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="939e3-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="939e3-117">Requirements</span></span>  
 <span data-ttu-id="939e3-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="939e3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="939e3-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="939e3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="939e3-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="939e3-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="939e3-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="939e3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939e3-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="939e3-122">See also</span></span>

- [<span data-ttu-id="939e3-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="939e3-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
