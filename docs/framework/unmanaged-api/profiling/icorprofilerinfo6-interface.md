---
title: ICorProfilerInfo6, interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868372"
---
# <a name="icorprofilerinfo6-interface"></a><span data-ttu-id="26adf-102">ICorProfilerInfo6, interfejs</span><span class="sxs-lookup"><span data-stu-id="26adf-102">ICorProfilerInfo6 Interface</span></span>
<span data-ttu-id="26adf-103">[Obsługiwane w .NET Framework 4,6 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="26adf-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="26adf-104">Podklasa elementu [ICorProfilerInfo5](icorprofilerinfo5-interface.md) , która dostarcza moduł wyliczający dla wszystkich metod, które są zdefiniowane w danym module NGen i w sposób wbudowany daną metodę.</span><span class="sxs-lookup"><span data-stu-id="26adf-104">A subclass of [ICorProfilerInfo5](icorprofilerinfo5-interface.md) that provides an enumerator for all methods that are defined in a given NGen module and inline a given method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26adf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="26adf-105">Methods</span></span>  
  
|<span data-ttu-id="26adf-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="26adf-106">Method</span></span>|<span data-ttu-id="26adf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="26adf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26adf-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="26adf-108">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|<span data-ttu-id="26adf-109">Zwraca moduł wyliczający dla wszystkich metod, które należą do danego modułu NGen i są zawarte w treści danej metody.</span><span class="sxs-lookup"><span data-stu-id="26adf-109">Returns an enumerator for all methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26adf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26adf-110">Requirements</span></span>  
 <span data-ttu-id="26adf-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26adf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26adf-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26adf-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26adf-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26adf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26adf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26adf-114">See also</span></span>

- [<span data-ttu-id="26adf-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="26adf-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
