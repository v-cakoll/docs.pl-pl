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
ms.openlocfilehash: 514488c6e0d2e89de0d8ee483def485ec9f3ef25
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009109"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="c588e-102">IMetaDataAssemblyImport::EnumExportedTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="c588e-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="c588e-103">Wylicza eksportowane typy, do których odwołuje się manifest zestawu w bieżącym zakresie metadanych.</span><span class="sxs-lookup"><span data-stu-id="c588e-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c588e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c588e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,
    [out] mdExportedType   rExportedTypes[],
    [in]  ULONG            cMax,
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c588e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c588e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c588e-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c588e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c588e-107">Ta wartość musi być wartością null, gdy `EnumExportedTypes` Metoda jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c588e-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="c588e-108">określoną Wyliczanie `mdExportedType` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="c588e-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c588e-109">podczas Maksymalna liczba `mdExportedType` tokenów, które mogą zostać umieszczone w `rExportedTypes` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c588e-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c588e-110">określoną Liczba `mdExportedType` tokenów, które zostały umieszczone w rzeczywistości `rExportedTypes` .</span><span class="sxs-lookup"><span data-stu-id="c588e-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c588e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c588e-111">Return Value</span></span>  
  
|<span data-ttu-id="c588e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c588e-112">HRESULT</span></span>|<span data-ttu-id="c588e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c588e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c588e-114">`EnumExportedTypes`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="c588e-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c588e-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c588e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c588e-116">W tym przypadku `pcTokens` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="c588e-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c588e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c588e-117">Requirements</span></span>  
 <span data-ttu-id="c588e-118">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c588e-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c588e-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c588e-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c588e-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c588e-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c588e-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c588e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c588e-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c588e-122">See also</span></span>

- [<span data-ttu-id="c588e-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c588e-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
