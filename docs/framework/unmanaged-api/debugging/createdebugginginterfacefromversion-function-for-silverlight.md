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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77164f9d8a1641ba37fa504d09d77ec6aecc3db5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965818"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="a4d43-102">CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="a4d43-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="a4d43-103">Akceptuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) wersja ciąg, który jest zwracany z [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedniego interfejsu debugera (zazwyczaj [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="a4d43-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4d43-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4d43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4d43-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="a4d43-106">[in] Ciąg wersji środowiska CLR w debugowanym obiekcie docelowym, która jest zwracana przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a4d43-107">[out] Wskaźnik do wskaźnika do obiektu COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="a4d43-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="a4d43-108">Ten obiekt zostanie rzutowany [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="a4d43-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4d43-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4d43-109">Return Value</span></span>  
 <span data-ttu-id="a4d43-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4d43-110">S_OK</span></span>  
 <span data-ttu-id="a4d43-111">`ppCordb` odwołuje się do prawidłowego obiektu, który implementuje [icordebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a4d43-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a4d43-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a4d43-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="a4d43-113">Albo `szDebuggeeVersion` lub `ppCordb` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a4d43-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="a4d43-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="a4d43-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="a4d43-115">Składnik, który jest konieczny, aby debugowanie CLR nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="a4d43-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="a4d43-116">Oznacza to, że plik mscordbi.dll lub mscordaccore.dll nie został znaleziony w tym samym katalogu jako element docelowy CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="a4d43-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a4d43-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="a4d43-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="a4d43-118">Plik mscordbi.dll lub mscordaccore.dll nie jest tę samą wersję, jako cel CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="a4d43-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a4d43-119">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="a4d43-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a4d43-120">Nie można zwrócić [icordebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4d43-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4d43-121">Remarks</span></span>  
 <span data-ttu-id="a4d43-122">Interfejs, który jest zwracany udostępnia funkcje służące do dołączania do CLR w procesie docelowym i debugowania kodu zarządzanego, który działa środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a4d43-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d43-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4d43-123">Requirements</span></span>  
 <span data-ttu-id="a4d43-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d43-125">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="a4d43-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a4d43-126">**Biblioteka:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="a4d43-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a4d43-127">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="a4d43-127">**.NET Framework Versions:** 3.5 SP1</span></span>
