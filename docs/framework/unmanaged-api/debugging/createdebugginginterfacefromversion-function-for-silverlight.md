---
title: CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: 85b5a5a630f399d0e036de434365e2e4f8f02dea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793829"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="9c5a4-102">CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="9c5a4-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="9c5a4-103">Akceptuje ciąg wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest zwracany przez [funkcję CreateVersionStringFromModule —](createversionstringfrommodule-function.md)i zwraca odpowiedni interfejs debugera (zazwyczaj [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="9c5a4-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c5a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c5a4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c5a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9c5a4-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="9c5a4-106">podczas Ciąg wersji środowiska CLR w docelowym debugowanego obiektu, który jest zwracany przez [funkcję CreateVersionStringFromModule —](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="9c5a4-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="9c5a4-107">określoną Wskaźnik na wskaźnik do obiektu COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="9c5a4-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="9c5a4-108">Ten obiekt będzie rzutowany na obiekt [ICorDebug](icordebug-interface.md) przed jego zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c5a4-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="9c5a4-109">Return Value</span></span>  
 <span data-ttu-id="9c5a4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9c5a4-110">S_OK</span></span>  
 <span data-ttu-id="9c5a4-111">`ppCordb` odwołuje się do prawidłowego obiektu, który implementuje interfejs [interfejsu ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9c5a4-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="9c5a4-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9c5a4-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="9c5a4-113">`szDebuggeeVersion` lub `ppCordb` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="9c5a4-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="9c5a4-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="9c5a4-115">Nie można zlokalizować składnika, który jest niezbędny do debugowania CLR.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="9c5a4-116">Oznacza to, że plik mscordbi. dll lub mscordaccore. dll nie został odnaleziony w tym samym katalogu co element docelowy CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="9c5a4-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="9c5a4-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="9c5a4-118">Mscordbi. dll lub mscordaccore. dll nie jest taka sama jak wersja elementu docelowego CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="9c5a4-119">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="9c5a4-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9c5a4-120">Nie można zwrócić [interfejsu ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9c5a4-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c5a4-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c5a4-121">Remarks</span></span>  
 <span data-ttu-id="9c5a4-122">Interfejs, który jest zwracany, udostępnia funkcje do dołączania do środowiska CLR w procesie docelowym i debugowania kodu zarządzanego, który działa środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="9c5a4-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c5a4-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9c5a4-123">Requirements</span></span>  
 <span data-ttu-id="9c5a4-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c5a4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c5a4-125">**Nagłówek:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="9c5a4-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="9c5a4-126">**Biblioteka:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="9c5a4-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="9c5a4-127">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="9c5a4-127">**.NET Framework Versions:** 3.5 SP1</span></span>
