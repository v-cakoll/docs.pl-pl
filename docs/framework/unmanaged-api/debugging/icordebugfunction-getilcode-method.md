---
title: ICorDebugFunction::GetILCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f34a2fe2bb1f92e75f77c086b03776ec59495600
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482109"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="f1584-102">ICorDebugFunction::GetILCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1584-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="f1584-103">Pobiera wystąpienie ICorDebugCode, który reprezentuje kod intermediate language (MSIL) firmy Microsoft, które są skojarzone z tym obiektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="f1584-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1584-104">Syntax</span></span>  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1584-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1584-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="f1584-106">[out] Wskaźnik do `ICorDebugCode` wystąpienia lub wartość null, jeśli funkcja nie został skompilowany w MSIL.</span><span class="sxs-lookup"><span data-stu-id="f1584-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1584-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1584-107">Remarks</span></span>  
 <span data-ttu-id="f1584-108">Jeśli zezwolono Edytuj i Kontynuuj dla tej funkcji `GetILCode` metody zostanie wyświetlony kod MSIL odpowiadający tej funkcji edytowaną wersją kodu w środowisku uruchomieniowym języka (wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="f1584-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1584-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1584-109">Requirements</span></span>  
 <span data-ttu-id="f1584-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1584-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1584-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1584-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1584-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1584-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1584-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1584-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
