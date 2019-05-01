---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782983"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="68fcb-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="68fcb-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="68fcb-103">Zwraca adres podstawowy moduł i rozmiar z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="68fcb-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68fcb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68fcb-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68fcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68fcb-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="68fcb-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="68fcb-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="68fcb-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="68fcb-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="68fcb-108">Wskaźnik do rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="68fcb-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68fcb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68fcb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68fcb-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="68fcb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68fcb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68fcb-111">Requirements</span></span>  
 <span data-ttu-id="68fcb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68fcb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68fcb-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68fcb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68fcb-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68fcb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68fcb-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68fcb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fcb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68fcb-116">See also</span></span>

- [<span data-ttu-id="68fcb-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="68fcb-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="68fcb-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="68fcb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
