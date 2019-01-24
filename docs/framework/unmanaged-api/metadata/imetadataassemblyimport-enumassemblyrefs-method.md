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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d10fb391953e924feb553ae4516fb7674345ed3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592019"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="8c77f-102">IMetaDataAssemblyImport::EnumAssemblyRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c77f-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="8c77f-103">Wylicza `mdAssemblyRef` wystąpień, które są zdefiniowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="8c77f-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c77f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c77f-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c77f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c77f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8c77f-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8c77f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8c77f-107">Musi to być wartość null wartość przy `EnumAssemblyRefs` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="8c77f-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="8c77f-108">[out] Wyliczanie `mdAssemblyRef` tokeny metadanych.</span><span class="sxs-lookup"><span data-stu-id="8c77f-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8c77f-109">[in] Maksymalna liczba tokenów, które można umieścić w `rAssemblyRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8c77f-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8c77f-110">[out] Liczba tokenów faktycznie umieszczone w `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="8c77f-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c77f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8c77f-111">Return Value</span></span>  
  
|<span data-ttu-id="8c77f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c77f-112">HRESULT</span></span>|<span data-ttu-id="8c77f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8c77f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8c77f-114">`EnumAssemblyRefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="8c77f-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8c77f-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8c77f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8c77f-116">W tym przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="8c77f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c77f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c77f-117">Requirements</span></span>  
 <span data-ttu-id="8c77f-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c77f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c77f-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8c77f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c77f-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c77f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c77f-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c77f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c77f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c77f-122">See also</span></span>
- [<span data-ttu-id="8c77f-123">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c77f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
