---
title: IMetaDataImport::GetUserString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edeaefd0792a5cc03ae6d4385ff669a343ffdfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778809"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="bed4e-102">IMetaDataImport::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="bed4e-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="bed4e-103">Pobiera ciąg literału, reprezentowane przez token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="bed4e-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bed4e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bed4e-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="bed4e-106">[in] Token ciągu do zwrócenia skojarzony ciąg.</span><span class="sxs-lookup"><span data-stu-id="bed4e-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="bed4e-107">[out] Kopia żądanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="bed4e-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="bed4e-108">[in] Maksymalny rozmiar w znaki dwubajtowe dla żądanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="bed4e-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="bed4e-109">[out] Rozmiar w znaki dwubajtowe zwracanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="bed4e-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed4e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bed4e-110">Requirements</span></span>  
 <span data-ttu-id="bed4e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed4e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed4e-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bed4e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bed4e-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bed4e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bed4e-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed4e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed4e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bed4e-115">See also</span></span>

- [<span data-ttu-id="bed4e-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="bed4e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bed4e-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bed4e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
