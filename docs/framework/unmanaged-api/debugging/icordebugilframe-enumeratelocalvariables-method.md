---
title: ICorDebugILFrame::EnumerateLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178845"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="ec5ee-102">ICorDebugILFrame::EnumerateLocalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec5ee-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="ec5ee-103">Pobiera wyliczenia dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec5ee-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec5ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec5ee-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="ec5ee-106">[na zewnątrz] Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest wyliczaczem zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec5ee-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec5ee-107">Remarks</span></span>  
 <span data-ttu-id="ec5ee-108">`EnumerateLocalVariables`pobiera wyliczenia, który można wyświetlić listę zmiennych lokalnych dostępnych w ramce wywołania, który jest reprezentowany przez ten obiekt ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="ec5ee-109">Lista może nie zawierać wszystkich zmiennych lokalnych w uruchomionej funkcji, ponieważ niektóre z nich mogą nie być aktywne.</span><span class="sxs-lookup"><span data-stu-id="ec5ee-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec5ee-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec5ee-110">Requirements</span></span>  
 <span data-ttu-id="ec5ee-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec5ee-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec5ee-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec5ee-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec5ee-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec5ee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec5ee-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec5ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
