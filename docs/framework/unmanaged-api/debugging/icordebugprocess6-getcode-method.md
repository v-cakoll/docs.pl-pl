---
title: Metoda ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 178d1df7e6c8246b18afed442e944c49051b6597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209269"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="a1643-102">Metoda ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="a1643-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="a1643-103">Pobiera informacje o zarządzanym kodzie pod określonym adresem kodu.</span><span class="sxs-lookup"><span data-stu-id="a1643-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1643-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1643-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1643-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1643-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="a1643-106">podczas Wartość [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , która określa adres początkowy segmentu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a1643-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="a1643-107">określoną Wskaźnik do adresu obiektu "ICorDebugCode", który reprezentuje segment kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a1643-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1643-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1643-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1643-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a1643-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1643-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1643-110">Requirements</span></span>  
 <span data-ttu-id="a1643-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1643-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1643-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1643-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1643-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1643-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1643-114">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1643-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1643-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1643-115">See also</span></span>

- [<span data-ttu-id="a1643-116">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="a1643-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="a1643-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1643-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
