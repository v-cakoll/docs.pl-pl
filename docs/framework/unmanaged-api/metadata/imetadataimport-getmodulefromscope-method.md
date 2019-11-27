---
title: IMetaDataImport::GetModuleFromScope — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 026a952e14cda2ef4ebc32ca91006026e920e3c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437360"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="6d3e3-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d3e3-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="6d3e3-103">Pobiera token metadanych dla modułu, do którego odwołuje się bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d3e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d3e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d3e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d3e3-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="6d3e3-106">określoną Wskaźnik do tokenu reprezentującego moduł, do którego odwołuje się bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="6d3e3-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d3e3-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d3e3-107">Requirements</span></span>  
 <span data-ttu-id="6d3e3-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d3e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d3e3-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d3e3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d3e3-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6d3e3-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d3e3-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d3e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3e3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d3e3-112">See also</span></span>

- [<span data-ttu-id="6d3e3-113">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d3e3-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6d3e3-114">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d3e3-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
