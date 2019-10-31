---
title: Metoda ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: fc7fecc3f523d7992bd57e2f7d485648caa6df8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123468"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="432f8-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="432f8-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="432f8-103">Pobiera informacje o zarządzanym kodzie pod określonym adresem kodu.</span><span class="sxs-lookup"><span data-stu-id="432f8-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="432f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="432f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="432f8-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="432f8-106">podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która określa adres początkowy segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="432f8-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="432f8-107">określoną Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="432f8-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="432f8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="432f8-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="432f8-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="432f8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="432f8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="432f8-110">Requirements</span></span>  
 <span data-ttu-id="432f8-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="432f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="432f8-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="432f8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="432f8-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="432f8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="432f8-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="432f8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432f8-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="432f8-115">See also</span></span>

- [<span data-ttu-id="432f8-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="432f8-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="432f8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="432f8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
