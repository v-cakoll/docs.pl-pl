---
title: IMetaDataImport::GetModuleRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f46033b9e643ef6b4a0063c4995b8c024b8c1f7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175359"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="810dc-102">IMetaDataImport::GetModuleRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="810dc-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="810dc-103">Pobiera nazwę modułu, do którego odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="810dc-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="810dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="810dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="810dc-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="810dc-106">[w] ModułRef token metadanych, który odwołuje się do modułu, aby uzyskać informacje o metadanych.</span><span class="sxs-lookup"><span data-stu-id="810dc-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="810dc-107">[na zewnątrz] Bufor do przechowywania nazwy modułu.</span><span class="sxs-lookup"><span data-stu-id="810dc-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="810dc-108">[w] Żądany rozmiar `szName` w szerokich znakach.</span><span class="sxs-lookup"><span data-stu-id="810dc-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="810dc-109">[na zewnątrz] Zwrócony rozmiar `szName` w szerokich znakach.</span><span class="sxs-lookup"><span data-stu-id="810dc-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810dc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="810dc-110">Requirements</span></span>  
 <span data-ttu-id="810dc-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="810dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="810dc-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="810dc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="810dc-113">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="810dc-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="810dc-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="810dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810dc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="810dc-115">See also</span></span>

- [<span data-ttu-id="810dc-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="810dc-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="810dc-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="810dc-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
