---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 58ad041b1243fabdc1948342730c81c5b8ff0991
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122139"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="ee4c3-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="ee4c3-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="ee4c3-103">Zwraca adres podstawowy i rozmiar modułu z adresu w tym module.</span><span class="sxs-lookup"><span data-stu-id="ee4c3-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee4c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee4c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee4c3-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="ee4c3-106">Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="ee4c3-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="ee4c3-107">określoną Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="ee4c3-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="ee4c3-108">Wskaźnik do rozmiaru modułu.</span><span class="sxs-lookup"><span data-stu-id="ee4c3-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee4c3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee4c3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee4c3-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ee4c3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4c3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee4c3-111">Requirements</span></span>  
 <span data-ttu-id="ee4c3-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee4c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4c3-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee4c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee4c3-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ee4c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee4c3-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4c3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4c3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee4c3-116">See also</span></span>

- [<span data-ttu-id="ee4c3-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee4c3-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="ee4c3-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ee4c3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
