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
ms.openlocfilehash: c2ce4b95de75bef3928e144656b565676568caa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137909"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="bf6cc-102">ICorDebugFunction::GetILCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf6cc-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="bf6cc-103">Pobiera wystąpienie ICorDebugCode, które reprezentuje kod języka pośredniego firmy Microsoft (MSIL) skojarzony z tym obiektem ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="bf6cc-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf6cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf6cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf6cc-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="bf6cc-106">określoną Wskaźnik do wystąpienia `ICorDebugCode` lub wartość null, jeśli funkcja nie została skompilowana do MSIL.</span><span class="sxs-lookup"><span data-stu-id="bf6cc-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf6cc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf6cc-107">Remarks</span></span>  
 <span data-ttu-id="bf6cc-108">Jeśli funkcja Edytuj i Kontynuuj jest dozwolona dla tej funkcji, Metoda `GetILCode` pobierze kod MSIL odpowiadający edytowanej wersji kodu w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="bf6cc-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6cc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf6cc-109">Requirements</span></span>  
 <span data-ttu-id="bf6cc-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf6cc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6cc-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf6cc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf6cc-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bf6cc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf6cc-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf6cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
