---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72bad186bc8bb198a8c5b05fffcc0b2b6544482f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472424"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="7e0db-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="7e0db-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="7e0db-103">Zwraca adres podstawowy moduł i rozmiar z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="7e0db-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e0db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e0db-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e0db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e0db-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="7e0db-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="7e0db-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="7e0db-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="7e0db-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="7e0db-108">Wskaźnik do rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="7e0db-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e0db-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e0db-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e0db-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7e0db-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e0db-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e0db-111">Requirements</span></span>  
 <span data-ttu-id="7e0db-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e0db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0db-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e0db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e0db-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e0db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e0db-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0db-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0db-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e0db-116">See also</span></span>
- [<span data-ttu-id="7e0db-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e0db-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="7e0db-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7e0db-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
