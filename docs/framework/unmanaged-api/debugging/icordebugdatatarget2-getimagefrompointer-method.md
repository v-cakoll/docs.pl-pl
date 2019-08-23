---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2371072261c9c75436ab86d742ce75423587765
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969440"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="a487d-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="a487d-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="a487d-103">Zwraca adres podstawowy i rozmiar modułu z adresu w tym module.</span><span class="sxs-lookup"><span data-stu-id="a487d-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a487d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a487d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a487d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a487d-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="a487d-106">Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="a487d-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="a487d-107">określoną Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="a487d-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="a487d-108">Wskaźnik do rozmiaru modułu.</span><span class="sxs-lookup"><span data-stu-id="a487d-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a487d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a487d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a487d-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a487d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a487d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a487d-111">Requirements</span></span>  
 <span data-ttu-id="a487d-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a487d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a487d-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a487d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a487d-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a487d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a487d-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a487d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a487d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a487d-116">See also</span></span>

- [<span data-ttu-id="a487d-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a487d-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="a487d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a487d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
