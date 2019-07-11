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
ms.openlocfilehash: 44d3fee49ae74c69b49029208588f4894e250f78
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775212"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="81b3b-102">ICorProfilerModuleEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="81b3b-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="81b3b-103">Pobiera liczbę modułów zarządzanych, które zostały załadowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81b3b-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81b3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81b3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81b3b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="81b3b-106">[out] Liczba modułów środowiska uruchomieniowego w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="81b3b-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81b3b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81b3b-107">Requirements</span></span>  
 <span data-ttu-id="81b3b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81b3b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81b3b-109">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81b3b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81b3b-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81b3b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81b3b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81b3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b3b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81b3b-112">See also</span></span>

- [<span data-ttu-id="81b3b-113">ICorProfilerModuleEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="81b3b-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="81b3b-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="81b3b-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
