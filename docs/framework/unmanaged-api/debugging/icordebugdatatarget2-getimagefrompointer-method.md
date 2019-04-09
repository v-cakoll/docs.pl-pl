---
title: Metoda ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154378"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="ec872-102">Metoda ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="ec872-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="ec872-103">Zwraca adres podstawowy moduł i rozmiar z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="ec872-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec872-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec872-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec872-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec872-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="ec872-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres w module.</span><span class="sxs-lookup"><span data-stu-id="ec872-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="ec872-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="ec872-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="ec872-108">Wskaźnik do rozmiar modułu.</span><span class="sxs-lookup"><span data-stu-id="ec872-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec872-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec872-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ec872-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec872-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec872-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec872-111">Requirements</span></span>  
 <span data-ttu-id="ec872-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec872-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec872-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec872-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec872-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec872-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ec872-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ec872-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ec872-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec872-116">See also</span></span>

- [<span data-ttu-id="ec872-117">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="ec872-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="ec872-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ec872-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
