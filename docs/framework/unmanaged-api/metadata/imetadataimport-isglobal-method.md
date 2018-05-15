---
title: IMetaDataImport::IsGlobal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4156c3507ccbd21d59893c5e03e15fe9b7322e48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="dc6ad-102">IMetaDataImport::IsGlobal — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc6ad-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="dc6ad-103">Pobiera wartość wskazującą, czy pola, metody lub typu reprezentowanego przez token określonych metadanych, ma zasięg globalny.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc6ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc6ad-104">Syntax</span></span>  
  
```  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc6ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc6ad-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="dc6ad-106">[in] Token metadanych, który reprezentuje typ, pole lub metoda.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="dc6ad-107">[out] 1, gdy obiekt ma zasięg globalny; w przeciwnym razie wartość 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="dc6ad-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc6ad-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc6ad-108">Requirements</span></span>  
 <span data-ttu-id="dc6ad-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc6ad-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc6ad-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc6ad-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc6ad-111">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc6ad-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc6ad-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc6ad-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc6ad-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc6ad-113">See Also</span></span>  
 [<span data-ttu-id="dc6ad-114">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc6ad-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="dc6ad-115">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc6ad-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
