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
ms.openlocfilehash: 358346af540c8b6b7ee1523e763bebbacf8cd2bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127819"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="77e58-102">IMetaDataImport::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="77e58-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="77e58-103">Pobiera ciąg literału, reprezentowane przez token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="77e58-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77e58-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77e58-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="77e58-106">[in] Token ciągu do zwrócenia skojarzony ciąg.</span><span class="sxs-lookup"><span data-stu-id="77e58-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="77e58-107">[out] Kopia żądanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="77e58-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="77e58-108">[in] Maksymalny rozmiar w znaki dwubajtowe dla żądanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="77e58-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="77e58-109">[out] Rozmiar w znaki dwubajtowe zwracanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="77e58-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e58-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77e58-110">Requirements</span></span>  
 <span data-ttu-id="77e58-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77e58-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e58-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="77e58-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77e58-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77e58-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="77e58-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="77e58-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77e58-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77e58-115">See also</span></span>

- [<span data-ttu-id="77e58-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="77e58-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="77e58-117">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="77e58-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
