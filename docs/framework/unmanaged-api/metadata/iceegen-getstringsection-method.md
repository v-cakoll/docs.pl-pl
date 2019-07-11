---
title: ICeeGen::GetStringSection — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68dc80c657c3794a416f6e142f70cfb05bee2c77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745894"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="7e01e-102">ICeeGen::GetStringSection — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e01e-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="7e01e-103">Pobiera reprezentację ciągu sekcję kodu przywoływane przez określone dojście.</span><span class="sxs-lookup"><span data-stu-id="7e01e-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="7e01e-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="7e01e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e01e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e01e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e01e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e01e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7e01e-107">[out w] Dojście do sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="7e01e-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e01e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e01e-108">Requirements</span></span>  
 <span data-ttu-id="7e01e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e01e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e01e-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7e01e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e01e-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e01e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e01e-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e01e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e01e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e01e-113">See also</span></span>

- [<span data-ttu-id="7e01e-114">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e01e-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
