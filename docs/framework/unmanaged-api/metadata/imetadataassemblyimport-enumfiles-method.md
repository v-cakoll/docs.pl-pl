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
ms.openlocfilehash: b2ab06419491093a2de41d2ef25d16c01c03ebaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158850"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="51fc9-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="51fc9-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="51fc9-103">Wylicza pliki, do którego odwołuje się do bieżącego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="51fc9-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51fc9-104">Syntax</span></span>  
  
```  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51fc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51fc9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="51fc9-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="51fc9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="51fc9-107">Musi to być wartość null w pierwszym wywołaniu tej metody.</span><span class="sxs-lookup"><span data-stu-id="51fc9-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="51fc9-108">[out] Tablica do przechowywania `mdFile` tokeny metadanych.</span><span class="sxs-lookup"><span data-stu-id="51fc9-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="51fc9-109">[in] Maksymalna liczba `mdFile` tokenów, które można umieścić w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="51fc9-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="51fc9-110">[out] Liczba `mdFile` tokenów faktycznie umieszczone w `rFiles`.</span><span class="sxs-lookup"><span data-stu-id="51fc9-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51fc9-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51fc9-111">Return Value</span></span>  
  
|<span data-ttu-id="51fc9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51fc9-112">HRESULT</span></span>|<span data-ttu-id="51fc9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="51fc9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="51fc9-114">`EnumFiles` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="51fc9-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="51fc9-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="51fc9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="51fc9-116">W tym przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="51fc9-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51fc9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51fc9-117">Requirements</span></span>  
 <span data-ttu-id="51fc9-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51fc9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51fc9-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="51fc9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51fc9-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51fc9-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51fc9-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51fc9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fc9-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51fc9-122">See also</span></span>

- [<span data-ttu-id="51fc9-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="51fc9-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
