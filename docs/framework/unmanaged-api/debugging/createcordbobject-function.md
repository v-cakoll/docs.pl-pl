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
ms.openlocfilehash: 1d190c5b558c7c523be09267e59eab7c5611563a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793857"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="55d94-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="55d94-102">CreateCordbObject Function</span></span>
<span data-ttu-id="55d94-103">Tworzy interfejs debugera ([ICorDebug](icordebug-interface.md)), który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.</span><span class="sxs-lookup"><span data-stu-id="55d94-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55d94-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,   
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55d94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55d94-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="55d94-106">podczas Wersja debugera procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="55d94-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="55d94-107">Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="55d94-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="55d94-108">określoną Wskaźnik na wskaźnik do obiektu, który będzie rzutowany do interfejsu [ICorDebug](icordebug-interface.md) i zwrócony.</span><span class="sxs-lookup"><span data-stu-id="55d94-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55d94-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="55d94-109">Return Value</span></span>  
 <span data-ttu-id="55d94-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="55d94-110">S_OK</span></span>  
 <span data-ttu-id="55d94-111">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="55d94-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="55d94-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="55d94-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="55d94-113">`ppCordb` ma wartość null lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="55d94-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="55d94-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="55d94-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="55d94-115">Nie można przydzielić wystarczającej ilości pamięci dla `ppCordb`</span><span class="sxs-lookup"><span data-stu-id="55d94-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="55d94-116">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="55d94-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="55d94-117">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="55d94-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55d94-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55d94-118">Remarks</span></span>  
 <span data-ttu-id="55d94-119">Interfejs [ICorDebug](icordebug-interface.md) , który jest zwracany w `ppCordb` jest interfejsem debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="55d94-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55d94-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55d94-120">Requirements</span></span>  
 <span data-ttu-id="55d94-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55d94-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55d94-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="55d94-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="55d94-123">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="55d94-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="55d94-124">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="55d94-124">**.NET Framework Versions:** 3.5 SP1</span></span>
