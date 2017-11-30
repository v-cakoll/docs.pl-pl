---
title: "CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1c37609d6fe95e95b19e6ab86bbb9ce4e9e1b87a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="57034-102">CreateDebuggingInterfaceFromVersion — Funkcja programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="57034-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="57034-103">Akceptuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) ciąg wersji zwrócone przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedniego interfejsu debugera (zazwyczaj [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="57034-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57034-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57034-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57034-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57034-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="57034-106">[in] Ciąg wersji aparatu CLR w debugowanym obiekcie docelowym, który jest zwracany przez [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="57034-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="57034-107">[out] Wskaźnik na wskaźnik do obiektu modelu COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="57034-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="57034-108">Ten obiekt będzie rzutowany [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt przed zwróceniem jest.</span><span class="sxs-lookup"><span data-stu-id="57034-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57034-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="57034-109">Return Value</span></span>  
 <span data-ttu-id="57034-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57034-110">S_OK</span></span>  
 <span data-ttu-id="57034-111">`ppCordb`odwołuje się do prawidłowego obiektu, który implementuje [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="57034-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="57034-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="57034-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="57034-113">Albo `szDebuggeeVersion` lub `ppCordb` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="57034-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="57034-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="57034-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="57034-115">Nie można zlokalizować składnika, który jest konieczny, aby debugowanie CLR.</span><span class="sxs-lookup"><span data-stu-id="57034-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="57034-116">Oznacza to, że plik mscordbi.dll lub mscordaccore.dll nie znaleziono w tym samym katalogu co element docelowy CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="57034-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="57034-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="57034-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="57034-118">Plik mscordbi.dll lub mscordaccore.dll nie jest ta sama wersja jako cel CoreCLR.dll.</span><span class="sxs-lookup"><span data-stu-id="57034-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="57034-119">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="57034-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="57034-120">Nie można zwrócić [ICorDebug — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="57034-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57034-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57034-121">Remarks</span></span>  
 <span data-ttu-id="57034-122">Interfejs, który jest zwracany zapewnia funkcji dołączanie do środowiska CLR w procesie docelowym i debugowanie kodu zarządzanego, uruchomionym środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="57034-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57034-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57034-123">Requirements</span></span>  
 <span data-ttu-id="57034-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57034-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57034-125">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="57034-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="57034-126">**Biblioteka:** biblioteki dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="57034-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="57034-127">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="57034-127">**.NET Framework Versions:** 3.5 SP1</span></span>
