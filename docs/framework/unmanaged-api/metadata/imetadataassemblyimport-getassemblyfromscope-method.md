---
title: IMetaDataAssemblyImport::GetAssemblyFromScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7322b4d0fce36f5dbef7e82f35cf9e2a1cae24a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="c9ad9-102">IMetaDataAssemblyImport::GetAssemblyFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9ad9-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="c9ad9-103">Pobiera wskaźnik do zestawu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="c9ad9-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ad9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9ad9-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9ad9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9ad9-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="c9ad9-106">[out] Wskaźnik do pobranej `mdAssembly` token, który identyfikuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="c9ad9-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9ad9-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9ad9-107">Requirements</span></span>  
 <span data-ttu-id="c9ad9-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ad9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ad9-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9ad9-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9ad9-110">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9ad9-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9ad9-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ad9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ad9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9ad9-112">See Also</span></span>  
 [<span data-ttu-id="c9ad9-113">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9ad9-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
