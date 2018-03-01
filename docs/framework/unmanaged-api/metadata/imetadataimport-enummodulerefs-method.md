---
title: "IMetaDataImport::EnumModuleRefs — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 782b363ddf518d45ac5e5fc2b2e4b1c68aff8ea3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="1a431-102">IMetaDataImport::EnumModuleRefs — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a431-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="1a431-103">Wylicza tokeny element ModuleRef, które reprezentują zaimportowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="1a431-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a431-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a431-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a431-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a431-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1a431-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1a431-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="1a431-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="1a431-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="1a431-108">[out] Tablica używany do przechowywania tokenów element ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="1a431-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1a431-109">[in] Maksymalny rozmiar `rModuleRefs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1a431-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="1a431-110">[out] Liczba tokenów element ModuleRef zwracane w `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="1a431-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a431-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a431-111">Return Value</span></span>  
  
|<span data-ttu-id="1a431-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a431-112">HRESULT</span></span>|<span data-ttu-id="1a431-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1a431-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1a431-114">`EnumModuleRefs`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1a431-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1a431-115">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1a431-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1a431-116">W takim przypadku `pcModuleRefs` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="1a431-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a431-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a431-117">Requirements</span></span>  
 <span data-ttu-id="1a431-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a431-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a431-119">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1a431-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a431-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a431-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a431-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a431-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a431-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a431-122">See Also</span></span>  
 [<span data-ttu-id="1a431-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a431-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1a431-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a431-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
