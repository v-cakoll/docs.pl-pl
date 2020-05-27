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
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009100"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="b10da-102">IMetaDataAssemblyImport::EnumFiles — Metoda</span><span class="sxs-lookup"><span data-stu-id="b10da-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="b10da-103">Wylicza pliki, do których odwołuje się bieżący manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b10da-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b10da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b10da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b10da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b10da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b10da-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b10da-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b10da-107">Musi to być wartość null dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="b10da-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="b10da-108">określoną Tablica służąca do przechowywania `mdFile` tokenów metadanych.</span><span class="sxs-lookup"><span data-stu-id="b10da-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b10da-109">podczas Maksymalna liczba `mdFile` tokenów, które mogą być umieszczone w `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="b10da-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b10da-110">określoną Liczba `mdFile` tokenów, które zostały umieszczone w rzeczywistości `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="b10da-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b10da-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b10da-111">Return Value</span></span>  
  
|<span data-ttu-id="b10da-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b10da-112">HRESULT</span></span>|<span data-ttu-id="b10da-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b10da-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b10da-114">`EnumFiles`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="b10da-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b10da-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b10da-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b10da-116">W tym przypadku `pcTokens` jest ustawiona na zero.</span><span class="sxs-lookup"><span data-stu-id="b10da-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b10da-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b10da-117">Requirements</span></span>  
 <span data-ttu-id="b10da-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b10da-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b10da-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b10da-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b10da-120">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b10da-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b10da-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b10da-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10da-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b10da-122">See also</span></span>

- [<span data-ttu-id="b10da-123">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b10da-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
