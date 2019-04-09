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
ms.openlocfilehash: 1cff5b7fadf4345b7a1d09911dc7061adc925e7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139155"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="377b5-102">ICeeGen::GetIlSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="377b5-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="377b5-103">Pobiera części bazy kodu języka pośredniego przywoływane przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="377b5-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="377b5-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="377b5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="377b5-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="377b5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="377b5-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="377b5-107">[in] Dojście do sekcji, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="377b5-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377b5-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="377b5-108">Requirements</span></span>  
 <span data-ttu-id="377b5-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="377b5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="377b5-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="377b5-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="377b5-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="377b5-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="377b5-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="377b5-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="377b5-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="377b5-113">See also</span></span>

- [<span data-ttu-id="377b5-114">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="377b5-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
