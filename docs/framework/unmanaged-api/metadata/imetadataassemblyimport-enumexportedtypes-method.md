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
ms.openlocfilehash: f00fe5bce2f808265add228406dfaa2ccc267545
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176009"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="c6668-102">IMetaDataAssemblyImport::EnumExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6668-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="c6668-103">Wylicza eksportowane typy, do których odwołuje się manifest zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6668-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6668-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6668-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6668-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6668-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c6668-106">[w, na zewnątrz] Wskaźnik do wyliczacza.</span><span class="sxs-lookup"><span data-stu-id="c6668-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c6668-107">Musi to być wartość `EnumExportedTypes` null, gdy metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c6668-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="c6668-108">[na zewnątrz] Wyliczenie tokenów `mdExportedType` metadanych.</span><span class="sxs-lookup"><span data-stu-id="c6668-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c6668-109">[w] Maksymalna liczba `mdExportedType` tokenów, które mogą `rExportedTypes` być umieszczone w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c6668-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c6668-110">[na zewnątrz] Liczba tokenów `mdExportedType` faktycznie umieszczonych w `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="c6668-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6668-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6668-111">Return Value</span></span>  
  
|<span data-ttu-id="c6668-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6668-112">HRESULT</span></span>|<span data-ttu-id="c6668-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c6668-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c6668-114">`EnumExportedTypes`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c6668-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c6668-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c6668-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c6668-116">W takim `pcTokens` przypadku jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="c6668-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6668-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6668-117">Requirements</span></span>  
 <span data-ttu-id="c6668-118">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6668-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6668-119">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6668-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6668-120">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6668-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6668-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6668-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6668-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6668-122">See also</span></span>

- [<span data-ttu-id="c6668-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c6668-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
