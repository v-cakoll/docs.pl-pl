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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777523"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="2b47d-102">IMetaDataImport::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b47d-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="2b47d-103">Pobiera ciąg literału, reprezentowane przez token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="2b47d-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b47d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b47d-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b47d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b47d-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="2b47d-106">[in] Token ciągu do zwrócenia skojarzony ciąg.</span><span class="sxs-lookup"><span data-stu-id="2b47d-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="2b47d-107">[out] Kopia żądanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="2b47d-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="2b47d-108">[in] Maksymalny rozmiar w znaki dwubajtowe dla żądanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="2b47d-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="2b47d-109">[out] Rozmiar w znaki dwubajtowe zwracanego `szString`.</span><span class="sxs-lookup"><span data-stu-id="2b47d-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b47d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b47d-110">Requirements</span></span>  
 <span data-ttu-id="2b47d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b47d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b47d-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2b47d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b47d-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b47d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b47d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b47d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b47d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b47d-115">See also</span></span>

- [<span data-ttu-id="2b47d-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b47d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2b47d-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b47d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
