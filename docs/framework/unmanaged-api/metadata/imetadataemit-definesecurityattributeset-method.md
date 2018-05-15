---
title: IMetaDataEmit::DefineSecurityAttributeSet — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60cb1640d374ce71d1d2fb51ba536b53ddd39b92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="b6ae4-102">IMetaDataEmit::DefineSecurityAttributeSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6ae4-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="b6ae4-103">Tworzy zestaw uprawnień zabezpieczeń, aby dołączyć do obiektu odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="b6ae4-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ae4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6ae4-104">Syntax</span></span>  
  
```  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6ae4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6ae4-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="b6ae4-106">[in] Token, do której jest dołączona informacji o zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="b6ae4-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="b6ae4-107">[in] Tablica `COR_SECATTR` struktury.</span><span class="sxs-lookup"><span data-stu-id="b6ae4-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="b6ae4-108">[in] Liczba elementów w `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="b6ae4-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="b6ae4-109">[out] Jeśli metoda nie powiedzie się, określa indeks w `rSecAttrs` elementu, który spowodował problem.</span><span class="sxs-lookup"><span data-stu-id="b6ae4-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ae4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6ae4-110">Requirements</span></span>  
 <span data-ttu-id="b6ae4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ae4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ae4-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6ae4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6ae4-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6ae4-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6ae4-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ae4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ae4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6ae4-115">See Also</span></span>  
 [<span data-ttu-id="b6ae4-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6ae4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b6ae4-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6ae4-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
