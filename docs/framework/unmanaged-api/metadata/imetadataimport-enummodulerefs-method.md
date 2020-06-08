---
title: IMetaDataImport::EnumModuleRefs — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491760"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="cbb41-102">IMetaDataImport::EnumModuleRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="cbb41-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="cbb41-103">Wylicza tokeny ModuleRef reprezentujące importowane moduły.</span><span class="sxs-lookup"><span data-stu-id="cbb41-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbb41-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbb41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbb41-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cbb41-106">[in. out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="cbb41-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cbb41-107">Musi ona mieć wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="cbb41-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="cbb41-108">określoną Tablica służąca do przechowywania tokenów ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="cbb41-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cbb41-109">podczas Maksymalny rozmiar `rModuleRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cbb41-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="cbb41-110">określoną Liczba tokenów elementu ModuleRef zwróconych w `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="cbb41-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbb41-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbb41-111">Return Value</span></span>  
  
|<span data-ttu-id="cbb41-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbb41-112">HRESULT</span></span>|<span data-ttu-id="cbb41-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cbb41-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cbb41-114">`EnumModuleRefs`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="cbb41-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cbb41-115">Brak tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cbb41-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cbb41-116">W takim przypadku `pcModuleRefs` jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="cbb41-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbb41-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbb41-117">Requirements</span></span>  
 <span data-ttu-id="cbb41-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb41-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb41-119">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cbb41-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbb41-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbb41-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbb41-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb41-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb41-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbb41-122">See also</span></span>

- [<span data-ttu-id="cbb41-123">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cbb41-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="cbb41-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbb41-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
