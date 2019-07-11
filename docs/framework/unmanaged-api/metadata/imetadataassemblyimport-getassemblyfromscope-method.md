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
ms.openlocfilehash: d40b997cd2b07cfc86e7671f7d7d2fcf9bd9c60a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772751"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="2030d-102">IMetaDataAssemblyImport::GetAssemblyFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="2030d-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="2030d-103">Pobiera wskaźnik do zestawu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="2030d-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2030d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2030d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2030d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2030d-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="2030d-106">[out] Wskaźnik do pobranych `mdAssembly` token, który identyfikuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="2030d-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2030d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2030d-107">Requirements</span></span>  
 <span data-ttu-id="2030d-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2030d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2030d-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2030d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2030d-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2030d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2030d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2030d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2030d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2030d-112">See also</span></span>

- [<span data-ttu-id="2030d-113">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="2030d-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
