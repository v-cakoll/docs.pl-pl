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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15606b8db740e79ad2bc0deb33afcb63ad839905
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466092"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="51ac1-102">IMetaDataImport::EnumModuleRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="51ac1-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="51ac1-103">Wylicza element ModuleRef tokenów, które reprezentują zaimportowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="51ac1-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ac1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51ac1-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51ac1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51ac1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="51ac1-106">[out w] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="51ac1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="51ac1-107">Musi to być wartość NULL dla pierwszego wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="51ac1-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="51ac1-108">[out] Tablica do przechowywania tokenów element ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="51ac1-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="51ac1-109">[in] Maksymalny rozmiar `rModuleRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="51ac1-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="51ac1-110">[out] Liczba tokenów element ModuleRef zwracane w `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="51ac1-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51ac1-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51ac1-111">Return Value</span></span>  
  
|<span data-ttu-id="51ac1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51ac1-112">HRESULT</span></span>|<span data-ttu-id="51ac1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="51ac1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="51ac1-114">`EnumModuleRefs` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="51ac1-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="51ac1-115">Nie ma żadnych tokeny do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="51ac1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="51ac1-116">W takim przypadku `pcModuleRefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="51ac1-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51ac1-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51ac1-117">Requirements</span></span>  
 <span data-ttu-id="51ac1-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51ac1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ac1-119">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="51ac1-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51ac1-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="51ac1-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51ac1-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ac1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ac1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51ac1-122">See also</span></span>
- [<span data-ttu-id="51ac1-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="51ac1-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="51ac1-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="51ac1-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
