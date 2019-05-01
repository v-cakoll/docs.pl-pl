---
title: ICorDebugMergedAssemblyRecord::GetPublicKey Method
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988120"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="6c9cc-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span><span class="sxs-lookup"><span data-stu-id="6c9cc-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="6c9cc-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="6c9cc-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c9cc-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c9cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c9cc-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="6c9cc-106">[in] Maksymalna liczba bajtów w `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6c9cc-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="6c9cc-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6c9cc-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="6c9cc-108">[out] Wskaźnik do tablicy typu byte, który zawiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="6c9cc-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c9cc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c9cc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c9cc-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6c9cc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9cc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c9cc-111">Requirements</span></span>  
 <span data-ttu-id="6c9cc-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c9cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9cc-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c9cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c9cc-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c9cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c9cc-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9cc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9cc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c9cc-116">See also</span></span>

- [<span data-ttu-id="6c9cc-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c9cc-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="6c9cc-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6c9cc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
