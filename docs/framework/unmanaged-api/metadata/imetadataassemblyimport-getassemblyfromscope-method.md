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
ms.openlocfilehash: adcaac02526c7d72ffb75ba6c7552632173032cf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009044"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="b2c8b-102">IMetaDataAssemblyImport::GetAssemblyFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2c8b-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="b2c8b-103">Pobiera wskaźnik do zestawu w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="b2c8b-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2c8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2c8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2c8b-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="b2c8b-106">określoną Wskaźnik do pobranego `mdAssembly` tokenu, który identyfikuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="b2c8b-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c8b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2c8b-107">Requirements</span></span>  
 <span data-ttu-id="b2c8b-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c8b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c8b-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b2c8b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2c8b-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b2c8b-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2c8b-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c8b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2c8b-112">See also</span></span>

- [<span data-ttu-id="b2c8b-113">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2c8b-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
