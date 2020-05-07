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
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860891"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="d5f2f-102">CreateCordbObject — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d5f2f-102">CreateCordbObject Function</span></span>
<span data-ttu-id="d5f2f-103">Tworzy interfejs debugera ([ICorDebug](icordebug-interface.md)), który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5f2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5f2f-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5f2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5f2f-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="d5f2f-106">podczas Wersja debugera procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="d5f2f-107">Ten parametr musi być CorDebugVersion_2_0 dla zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="d5f2f-108">określoną Wskaźnik na wskaźnik do obiektu, który będzie rzutowany do interfejsu [ICorDebug](icordebug-interface.md) i zwrócony.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5f2f-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5f2f-109">Return Value</span></span>  
 <span data-ttu-id="d5f2f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5f2f-110">S_OK</span></span>  
 <span data-ttu-id="d5f2f-111">Liczba CLRs w procesie została pomyślnie określona, a odpowiednie tablice uchwytów i ścieżek zostały prawidłowo wypełnione.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="d5f2f-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d5f2f-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="d5f2f-113">`ppCordb`ma wartość null lub `iDebuggerVersion` nie jest CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="d5f2f-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d5f2f-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="d5f2f-115">Nie można przydzielić wystarczającej ilości pamięci dla`ppCordb`</span><span class="sxs-lookup"><span data-stu-id="d5f2f-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="d5f2f-116">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="d5f2f-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d5f2f-117">Inne błędy.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5f2f-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5f2f-118">Remarks</span></span>  
 <span data-ttu-id="d5f2f-119">Interfejs [ICorDebug](icordebug-interface.md) , który jest zwracany w `ppCordb` programie, jest interfejsem debugowania najwyższego poziomu dla wszystkich zarządzanych usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="d5f2f-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5f2f-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5f2f-120">Requirements</span></span>  
 <span data-ttu-id="d5f2f-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5f2f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5f2f-122">**Nagłówek:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="d5f2f-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d5f2f-123">**Biblioteka:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="d5f2f-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d5f2f-124">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="d5f2f-124">**.NET Framework Versions:** 3.5 SP1</span></span>
