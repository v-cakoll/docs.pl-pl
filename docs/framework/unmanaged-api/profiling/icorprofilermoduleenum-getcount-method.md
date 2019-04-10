---
title: ICorProfilerModuleEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d246acbf314a83ca3f8113e9a2fb223ac0ebcafe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223709"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="ce7ac-102">ICorProfilerModuleEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce7ac-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="ce7ac-103">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce7ac-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce7ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce7ac-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce7ac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce7ac-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ce7ac-106">[out] Liczba modułów środowiska uruchomieniowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ce7ac-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce7ac-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce7ac-107">Requirements</span></span>  
 <span data-ttu-id="ce7ac-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce7ac-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce7ac-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce7ac-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce7ac-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce7ac-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ce7ac-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ce7ac-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce7ac-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce7ac-112">See also</span></span>

- [<span data-ttu-id="ce7ac-113">ICorProfilerModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ce7ac-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="ce7ac-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="ce7ac-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
