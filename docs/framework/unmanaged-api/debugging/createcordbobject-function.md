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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f546d7707c40f7f26a46177ae972a988e54e1e45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965837"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="93de2-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="93de2-102">CreateCordbObject Function</span></span>
<span data-ttu-id="93de2-103">Tworzy interfejs debugera ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) zapewnia funkcje tworzenia wystąpienia zarządzanego sesji debugowania zdalnego procesu.</span><span class="sxs-lookup"><span data-stu-id="93de2-103">Creates a debugger interface ([ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93de2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93de2-104">Syntax</span></span>  
  
```  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93de2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93de2-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="93de2-106">[in] Wersja debugera procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="93de2-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="93de2-107">Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="93de2-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="93de2-108">[out] Wskaźnik do wskaźnika do obiektu, który będzie można rzutować [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs i zwracana.</span><span class="sxs-lookup"><span data-stu-id="93de2-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93de2-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93de2-109">Return Value</span></span>  
 <span data-ttu-id="93de2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93de2-110">S_OK</span></span>  
 <span data-ttu-id="93de2-111">CLRs procesu został pomyślnie określana i odpowiednie dojścia i tablice ścieżki zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="93de2-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="93de2-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="93de2-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="93de2-113">`ppCordb` ma wartość null, lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="93de2-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="93de2-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="93de2-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="93de2-115">Nie można przydzielić wystarczającej ilości pamięci do `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="93de2-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="93de2-116">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="93de2-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="93de2-117">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="93de2-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93de2-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93de2-118">Remarks</span></span>  
 <span data-ttu-id="93de2-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejs, który jest zwracany w `ppCordb` jest najwyższego poziomu interfejsu debugowania dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="93de2-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93de2-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93de2-120">Requirements</span></span>  
 <span data-ttu-id="93de2-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93de2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93de2-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="93de2-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="93de2-123">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="93de2-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="93de2-124">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="93de2-124">**.NET Framework Versions:** 3.5 SP1</span></span>
