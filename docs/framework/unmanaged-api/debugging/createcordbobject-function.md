---
title: CreateCordbObject — Funkcja
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179233"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="34402-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="34402-102">CreateCordbObject Function</span></span>
<span data-ttu-id="34402-103">Tworzy interfejs debugera[(ICorDebug),](icordebug-interface.md)który zapewnia funkcje tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.</span><span class="sxs-lookup"><span data-stu-id="34402-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34402-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34402-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34402-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34402-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="34402-106">[w] Debuger wersji procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="34402-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="34402-107">Ten parametr musi być CorDebugVersion_2_0 do zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="34402-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="34402-108">[na zewnątrz] Wskaźnik do wskaźnika do obiektu, który zostanie rzutowania do interfejsu [ICorDebug](icordebug-interface.md) i zwrócone.</span><span class="sxs-lookup"><span data-stu-id="34402-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34402-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34402-109">Return Value</span></span>  
 <span data-ttu-id="34402-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="34402-110">S_OK</span></span>  
 <span data-ttu-id="34402-111">Liczba clr w procesie została pomyślnie określona, a odpowiednie tablice dojścia i ścieżki zostały poprawnie wypełnione.</span><span class="sxs-lookup"><span data-stu-id="34402-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="34402-112">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="34402-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="34402-113">`ppCordb`jest null `iDebuggerVersion` lub nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="34402-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="34402-114">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="34402-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="34402-115">Nie można przydzielić wystarczającej ilości pamięci`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="34402-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="34402-116">E_FAIL (lub inne E_ kody zwrotne)</span><span class="sxs-lookup"><span data-stu-id="34402-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="34402-117">Inne awarie.</span><span class="sxs-lookup"><span data-stu-id="34402-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34402-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34402-118">Remarks</span></span>  
 <span data-ttu-id="34402-119">Interfejs [ICorDebug,](icordebug-interface.md) który `ppCordb` jest zwracany w jest interfejs debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="34402-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34402-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34402-120">Requirements</span></span>  
 <span data-ttu-id="34402-121">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34402-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34402-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="34402-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="34402-123">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="34402-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="34402-124">**Wersje .NET Framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="34402-124">**.NET Framework Versions:** 3.5 SP1</span></span>
