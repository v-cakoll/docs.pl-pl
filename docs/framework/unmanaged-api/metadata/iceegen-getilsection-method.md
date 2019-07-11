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
ms.openlocfilehash: 8bddb782e13b4e7400c7e4a8128dc333efc8141d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746177"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="d2a32-102">ICeeGen::GetIlSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2a32-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="d2a32-103">Pobiera części bazy kodu języka pośredniego przywoływane przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="d2a32-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="d2a32-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="d2a32-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a32-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2a32-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2a32-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2a32-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d2a32-107">[in] Dojście do sekcji, aby uzyskać.</span><span class="sxs-lookup"><span data-stu-id="d2a32-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a32-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2a32-108">Requirements</span></span>  
 <span data-ttu-id="d2a32-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2a32-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a32-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d2a32-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2a32-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2a32-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d2a32-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a32-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a32-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2a32-113">See also</span></span>

- [<span data-ttu-id="d2a32-114">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2a32-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
