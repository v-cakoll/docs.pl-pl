---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cc02c1f69235403e2f5df28168e17a70f183682
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762413"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="f7fbc-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span><span class="sxs-lookup"><span data-stu-id="f7fbc-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="f7fbc-103">Pobiera klucz publiczny zestawu token.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fbc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7fbc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7fbc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7fbc-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="f7fbc-106">[in] Maksymalna liczba bajtów w `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="f7fbc-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="f7fbc-108">[out] Wskaźnik do tablicy typu byte, który zawiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7fbc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7fbc-109">Remarks</span></span>  
 <span data-ttu-id="f7fbc-110">Token klucza publicznego zestawu jest ostatnich ośmiu bajtów skrótu SHA1 swojego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7fbc-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7fbc-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7fbc-112">Requirements</span></span>  
 <span data-ttu-id="f7fbc-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7fbc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7fbc-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7fbc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7fbc-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7fbc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7fbc-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7fbc-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fbc-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7fbc-117">See also</span></span>

- [<span data-ttu-id="f7fbc-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7fbc-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="f7fbc-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f7fbc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
