---
title: ICorDebugMemoryBuffer::GetStartAddress — metoda
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422936"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="38a40-102">ICorDebugMemoryBuffer::GetStartAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="38a40-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="38a40-103">Pobiera początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="38a40-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38a40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38a40-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38a40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38a40-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="38a40-106">[out] Wskaźnik do początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="38a40-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38a40-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38a40-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="38a40-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38a40-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38a40-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38a40-109">Requirements</span></span>  
 <span data-ttu-id="38a40-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38a40-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38a40-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38a40-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38a40-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38a40-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38a40-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38a40-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38a40-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38a40-114">See Also</span></span>  
 [<span data-ttu-id="38a40-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="38a40-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="38a40-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38a40-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
