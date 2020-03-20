---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178919"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="4f6b1-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="4f6b1-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="4f6b1-103">Zwraca adres podstawowy modułu i rozmiar z adresu w tym module.</span><span class="sxs-lookup"><span data-stu-id="4f6b1-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f6b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f6b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f6b1-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="4f6b1-106">Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) reprezentująca adres w module.</span><span class="sxs-lookup"><span data-stu-id="4f6b1-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="4f6b1-107">[na zewnątrz] Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) reprezentująca adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="4f6b1-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="4f6b1-108">Wskaźnik do rozmiaru modułu.</span><span class="sxs-lookup"><span data-stu-id="4f6b1-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f6b1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f6b1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f6b1-110">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4f6b1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f6b1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f6b1-111">Requirements</span></span>  
 <span data-ttu-id="4f6b1-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f6b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f6b1-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f6b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f6b1-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f6b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f6b1-115">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f6b1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f6b1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f6b1-116">See also</span></span>

- [<span data-ttu-id="4f6b1-117">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f6b1-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="4f6b1-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4f6b1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
