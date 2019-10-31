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
ms.openlocfilehash: d21e0d3d0370ec7c1b223be29099f6b99822463b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132103"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="3ddf9-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3ddf9-102">CreateCordbObject Function</span></span>
<span data-ttu-id="3ddf9-103">Tworzy interfejs debugera ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)), który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddf9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ddf9-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ddf9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ddf9-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="3ddf9-106">podczas Wersja debugera procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="3ddf9-107">Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="3ddf9-108">określoną Wskaźnik na wskaźnik do obiektu, który będzie rzutowany do interfejsu [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) i zwrócony.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ddf9-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ddf9-109">Return Value</span></span>  
 <span data-ttu-id="3ddf9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ddf9-110">S_OK</span></span>  
 <span data-ttu-id="3ddf9-111">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="3ddf9-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3ddf9-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="3ddf9-113">`ppCordb` ma wartość null lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="3ddf9-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3ddf9-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="3ddf9-115">Nie można przydzielić wystarczającej ilości pamięci dla `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="3ddf9-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="3ddf9-116">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="3ddf9-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3ddf9-117">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ddf9-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ddf9-118">Remarks</span></span>  
 <span data-ttu-id="3ddf9-119">Interfejs [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , który jest zwracany w `ppCordb` jest interfejsem debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="3ddf9-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ddf9-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ddf9-120">Requirements</span></span>  
 <span data-ttu-id="3ddf9-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ddf9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ddf9-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="3ddf9-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="3ddf9-123">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="3ddf9-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="3ddf9-124">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3ddf9-124">**.NET Framework Versions:** 3.5 SP1</span></span>
