---
title: "CreateCordbObject — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCoredbObject
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06e08148e5526d65d82eca52ffe8db66a4e7df6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createcordbobject-function"></a><span data-ttu-id="5a5e8-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5a5e8-102">CreateCordbObject Function</span></span>
<span data-ttu-id="5a5e8-103">Tworzy interfejs debugera ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) zapewnia funkcje w uruchamianiu sesji debugowania zarządzanego dla procesu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a5e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a5e8-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a5e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a5e8-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="5a5e8-106">[in] Wersja debugera procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="5a5e8-107">Ten parametr musi być CorDebugVersion_2_0 do zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="5a5e8-108">[out] Wskaźnik na wskaźnik do obiektu, który będzie można rzutować na [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu i zwracany.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a5e8-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5a5e8-109">Return Value</span></span>  
 <span data-ttu-id="5a5e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a5e8-110">S_OK</span></span>  
 <span data-ttu-id="5a5e8-111">CLRs procesu został pomyślnie określana i odpowiednie dojścia tablice ścieżki zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="5a5e8-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5a5e8-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="5a5e8-113">`ppCordb`ma wartość null, lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="5a5e8-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5a5e8-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="5a5e8-115">Nie można przydzielić wystarczającej ilości pamięci do`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="5a5e8-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="5a5e8-116">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="5a5e8-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5a5e8-117">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a5e8-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a5e8-118">Remarks</span></span>  
 <span data-ttu-id="5a5e8-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs, który jest zwracany w `ppCordb` jest najwyższego poziomu interfejsu debugowania dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="5a5e8-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5e8-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a5e8-120">Requirements</span></span>  
 <span data-ttu-id="5a5e8-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a5e8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a5e8-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="5a5e8-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="5a5e8-123">**Biblioteka:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="5a5e8-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="5a5e8-124">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="5a5e8-124">**.NET Framework Versions:** 3.5 SP1</span></span>
