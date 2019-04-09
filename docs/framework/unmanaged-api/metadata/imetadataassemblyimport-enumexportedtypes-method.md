---
title: IMetaDataAssemblyImport::EnumExportedTypes — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c32dcfe5d00e1d35f7c63aa98a33d26f6b179c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152688"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="b724b-102">IMetaDataAssemblyImport::EnumExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="b724b-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="b724b-103">Wylicza typy wyeksportowany, do którego odwołuje się do manifestu zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="b724b-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b724b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b724b-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b724b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b724b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b724b-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b724b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b724b-107">Musi to być wartość null wartość przy `EnumExportedTypes` metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="b724b-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="b724b-108">[out] Wyliczanie `mdExportedType` tokeny metadanych.</span><span class="sxs-lookup"><span data-stu-id="b724b-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b724b-109">[in] Maksymalna liczba `mdExportedType` tokenów, które można umieścić w `rExportedTypes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b724b-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b724b-110">[out] Liczba `mdExportedType` tokenów faktycznie umieszczone w `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="b724b-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b724b-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b724b-111">Return Value</span></span>  
  
|<span data-ttu-id="b724b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b724b-112">HRESULT</span></span>|<span data-ttu-id="b724b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b724b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes` <span data-ttu-id="b724b-114">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="b724b-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b724b-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b724b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b724b-116">W tym przypadku `pcTokens` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="b724b-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b724b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b724b-117">Requirements</span></span>  
 <span data-ttu-id="b724b-118">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b724b-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b724b-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b724b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b724b-120">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b724b-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="b724b-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b724b-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b724b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b724b-122">See also</span></span>

- [<span data-ttu-id="b724b-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b724b-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
