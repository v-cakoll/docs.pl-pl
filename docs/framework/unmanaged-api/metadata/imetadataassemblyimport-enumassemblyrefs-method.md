---
title: IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450349"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="54b66-102">IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="54b66-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="54b66-103">Wylicza `mdAssemblyRef` wystąpienia, które są zdefiniowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="54b66-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b66-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54b66-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54b66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54b66-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="54b66-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="54b66-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="54b66-107">Ta wartość musi być wartością null, gdy metoda `EnumAssemblyRefs` jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="54b66-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="54b66-108">określoną Wyliczanie tokenów metadanych `mdAssemblyRef`.</span><span class="sxs-lookup"><span data-stu-id="54b66-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="54b66-109">podczas Maksymalna liczba tokenów, które mogą być umieszczone w tablicy `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="54b66-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="54b66-110">określoną Liczba tokenów faktycznie umieszczonych w `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="54b66-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54b66-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="54b66-111">Return Value</span></span>  
  
|<span data-ttu-id="54b66-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54b66-112">HRESULT</span></span>|<span data-ttu-id="54b66-113">Opis</span><span class="sxs-lookup"><span data-stu-id="54b66-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="54b66-114">`EnumAssemblyRefs` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="54b66-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="54b66-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="54b66-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="54b66-116">W tym przypadku `pcTokens` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="54b66-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54b66-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54b66-117">Requirements</span></span>  
 <span data-ttu-id="54b66-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54b66-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54b66-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54b66-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54b66-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54b66-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54b66-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54b66-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54b66-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54b66-122">See also</span></span>

- [<span data-ttu-id="54b66-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="54b66-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
