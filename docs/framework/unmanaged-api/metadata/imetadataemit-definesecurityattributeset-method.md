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
ms.openlocfilehash: fadd1974cd4fa8a51a06700835f46df24e37d7fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175775"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="3b0dd-102">IMetaDataEmit::DefineSecurityAttributeSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b0dd-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="3b0dd-103">Tworzy zestaw uprawnień zabezpieczeń do dołączenia do obiektu, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="3b0dd-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b0dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b0dd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b0dd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b0dd-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="3b0dd-106">[w] Token, do którego dołączone są informacje o zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="3b0dd-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="3b0dd-107">[w] Tablica `COR_SECATTR` struktur.</span><span class="sxs-lookup"><span data-stu-id="3b0dd-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="3b0dd-108">[w] Liczba elementów `rSecAttrs`w programie .</span><span class="sxs-lookup"><span data-stu-id="3b0dd-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="3b0dd-109">[na zewnątrz] Jeśli metoda nie powiedzie się, określa indeks w `rSecAttrs` elemencie, który spowodował problem.</span><span class="sxs-lookup"><span data-stu-id="3b0dd-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b0dd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b0dd-110">Requirements</span></span>  
 <span data-ttu-id="3b0dd-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b0dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b0dd-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b0dd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b0dd-113">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b0dd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b0dd-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b0dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0dd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b0dd-115">See also</span></span>

- [<span data-ttu-id="3b0dd-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3b0dd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3b0dd-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b0dd-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
