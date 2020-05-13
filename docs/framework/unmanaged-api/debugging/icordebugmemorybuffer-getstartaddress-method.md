---
title: 'ICorDebugMemoryBuffer:: GetStartAddress, Metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 47369c744ee42fb03857a3e69063a04e4f509d0d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212350"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="6d720-102">ICorDebugMemoryBuffer:: GetStartAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="6d720-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="6d720-103">Pobiera początkowy adres bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d720-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d720-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d720-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d720-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d720-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6d720-106">określoną Wskaźnik do adresu początkowego bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d720-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d720-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d720-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6d720-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d720-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d720-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d720-109">Requirements</span></span>  
 <span data-ttu-id="6d720-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d720-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d720-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d720-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d720-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d720-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d720-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d720-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d720-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d720-114">See also</span></span>

- [<span data-ttu-id="6d720-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d720-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6d720-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d720-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
