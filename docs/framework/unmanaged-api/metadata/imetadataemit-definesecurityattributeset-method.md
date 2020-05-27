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
ms.openlocfilehash: c33ede841324820da16e33d35bbf5e8f8e75924f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009373"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="14755-102">IMetaDataEmit::DefineSecurityAttributeSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="14755-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="14755-103">Tworzy zestaw uprawnień zabezpieczeń do dołączenia do obiektu, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="14755-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14755-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14755-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14755-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14755-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="14755-106">podczas Token, do którego są dołączone informacje o zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="14755-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="14755-107">podczas Tablica `COR_SECATTR` struktur.</span><span class="sxs-lookup"><span data-stu-id="14755-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="14755-108">podczas Liczba elementów w `rSecAttrs` .</span><span class="sxs-lookup"><span data-stu-id="14755-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="14755-109">określoną Jeśli metoda zakończy się niepowodzeniem, określa indeks `rSecAttrs` elementu, który spowodował problem.</span><span class="sxs-lookup"><span data-stu-id="14755-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14755-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14755-110">Requirements</span></span>  
 <span data-ttu-id="14755-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14755-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14755-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="14755-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14755-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="14755-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14755-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14755-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14755-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14755-115">See also</span></span>

- [<span data-ttu-id="14755-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14755-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="14755-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="14755-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
