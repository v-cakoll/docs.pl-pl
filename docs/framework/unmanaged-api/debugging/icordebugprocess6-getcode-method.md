---
title: Metoda ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 94882c67752705f9f13b858ae3b386a19dc103a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178554"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="9fa09-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="9fa09-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="9fa09-103">Pobiera informacje o kodzie zarządzanym pod określonym adresem kodu.</span><span class="sxs-lookup"><span data-stu-id="9fa09-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fa09-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fa09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fa09-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="9fa09-106">[w] Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) określająca adres początkowy segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9fa09-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="9fa09-107">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9fa09-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fa09-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fa09-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fa09-109">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9fa09-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa09-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fa09-110">Requirements</span></span>  
 <span data-ttu-id="9fa09-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa09-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa09-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fa09-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fa09-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fa09-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fa09-114">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa09-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa09-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fa09-115">See also</span></span>

- [<span data-ttu-id="9fa09-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="9fa09-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="9fa09-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9fa09-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
