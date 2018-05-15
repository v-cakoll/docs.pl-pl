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
ms.openlocfilehash: 474338ff1780ce9b442208cd06f8b14bc411be5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="c476a-102">IMetaDataImport::GetUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="c476a-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="c476a-103">Pobiera ciąg literału reprezentowany przez token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="c476a-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c476a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c476a-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c476a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c476a-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="c476a-106">[in] Token ciągu do zwrócenia skojarzone ciąg.</span><span class="sxs-lookup"><span data-stu-id="c476a-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="c476a-107">[out] Kopia żądanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="c476a-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c476a-108">[in] Maksymalny rozmiar w znaki dwubajtowe liczby żądanych `szString`.</span><span class="sxs-lookup"><span data-stu-id="c476a-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="c476a-109">[out] Rozmiar w znaki dwubajtowe zwróconego elementu `szString`.</span><span class="sxs-lookup"><span data-stu-id="c476a-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c476a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c476a-110">Requirements</span></span>  
 <span data-ttu-id="c476a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c476a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c476a-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c476a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c476a-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c476a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c476a-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c476a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c476a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c476a-115">See Also</span></span>  
 [<span data-ttu-id="c476a-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c476a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c476a-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c476a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
