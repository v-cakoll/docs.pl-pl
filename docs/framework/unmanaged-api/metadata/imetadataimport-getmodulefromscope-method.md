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
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503591"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="c1463-102">IMetaDataImport::GetModuleFromScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1463-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="c1463-103">Pobiera token metadanych dla modułu, do którego odwołuje się bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="c1463-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1463-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1463-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1463-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1463-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="c1463-106">określoną Wskaźnik do tokenu reprezentującego moduł, do którego odwołuje się bieżący zakres metadanych.</span><span class="sxs-lookup"><span data-stu-id="c1463-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1463-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1463-107">Requirements</span></span>  
 <span data-ttu-id="c1463-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1463-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1463-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1463-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1463-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1463-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1463-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1463-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1463-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1463-112">See also</span></span>

- [<span data-ttu-id="c1463-113">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c1463-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c1463-114">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1463-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
