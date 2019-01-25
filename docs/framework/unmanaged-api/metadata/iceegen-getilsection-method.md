---
title: ICeeGen::GetIlSection — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e75f46d73e068c6bdaac6ae01740ecf589c97d42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635913"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="f7f8b-102">ICeeGen::GetIlSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7f8b-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="f7f8b-103">Pobiera części bazy kodu języka pośredniego przywoływane przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="f7f8b-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="f7f8b-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="f7f8b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f8b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7f8b-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7f8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7f8b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="f7f8b-107">[in] Dojście do sekcji, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="f7f8b-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7f8b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7f8b-108">Requirements</span></span>  
 <span data-ttu-id="f7f8b-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7f8b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7f8b-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f7f8b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7f8b-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7f8b-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7f8b-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7f8b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f8b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7f8b-113">See also</span></span>
- [<span data-ttu-id="f7f8b-114">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7f8b-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
