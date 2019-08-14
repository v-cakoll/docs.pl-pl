---
title: ICorProfilerInfo9, interfejs
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 0ba4f2b4a515143d50bc812f04ea75d821b69471
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973688"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="cb2a3-102">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb2a3-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="cb2a3-103">Podklasa elementu [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) , która dostarcza metody do wykonywania zapytań o informacje o funkcjach z wieloma natywnymi wersjami kodu.</span><span class="sxs-lookup"><span data-stu-id="cb2a3-103">A subclass of [ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="cb2a3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cb2a3-104">Methods</span></span>  

| <span data-ttu-id="cb2a3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb2a3-105">Method</span></span>|<span data-ttu-id="cb2a3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cb2a3-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="cb2a3-107">GetNativeCodeStartAddresses, Metoda</span><span class="sxs-lookup"><span data-stu-id="cb2a3-107">GetNativeCodeStartAddresses Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="cb2a3-108">Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="cb2a3-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="cb2a3-109">GetILToNativeMapping3, Metoda</span><span class="sxs-lookup"><span data-stu-id="cb2a3-109">GetILToNativeMapping3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="cb2a3-110">Przy podanym adresie początkowym kodu natywnego program zwraca informacje mapowania natywnego do IL dla tej trybie JIT wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="cb2a3-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="cb2a3-111">GetCodeInfo4, Metoda</span><span class="sxs-lookup"><span data-stu-id="cb2a3-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="cb2a3-112">Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="cb2a3-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="cb2a3-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb2a3-113">Requirements</span></span>  
<span data-ttu-id="cb2a3-114">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="cb2a3-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
<span data-ttu-id="cb2a3-115">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb2a3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="cb2a3-116">**Wersje .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb2a3-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="cb2a3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb2a3-117">See also</span></span>
- [<span data-ttu-id="cb2a3-118">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cb2a3-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
