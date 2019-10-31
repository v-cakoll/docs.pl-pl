---
title: ICorDebugProcess::IsTransitionStub — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139389"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="16935-102">ICorDebugProcess::IsTransitionStub — Metoda</span><span class="sxs-lookup"><span data-stu-id="16935-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="16935-103">Pobiera wartość wskazującą, czy adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="16935-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16935-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16935-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16935-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16935-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="16935-106">podczas Wartość `CORDB_ADDRESS`, która określa dany adres.</span><span class="sxs-lookup"><span data-stu-id="16935-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="16935-107">określoną Wskaźnik do wartości logicznej, która jest `true`, jeśli określony adres znajduje się wewnątrz klasy zastępczej, która spowoduje przejście do kodu zarządzanego; w przeciwnym wypadku \*`pbTransitionStub` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="16935-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16935-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16935-108">Remarks</span></span>  
 <span data-ttu-id="16935-109">Metoda `IsTransitionStub` może być używana przez niezarządzany kod wykonujący, aby określić, kiedy należy zwrócić kontrolę krokową do zarządzanego stepper.</span><span class="sxs-lookup"><span data-stu-id="16935-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="16935-110">Można również posłużyć do przechodzenia między zmianami, sprawdzając informacje w przenośnym pliku wykonywalnym (PE).</span><span class="sxs-lookup"><span data-stu-id="16935-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16935-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16935-111">Requirements</span></span>  
 <span data-ttu-id="16935-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16935-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16935-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16935-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16935-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16935-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16935-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16935-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
