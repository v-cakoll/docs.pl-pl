---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 626aa53740839df0b47a876b3e82814a63ffd82d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936853"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="f2a41-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span><span class="sxs-lookup"><span data-stu-id="f2a41-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="f2a41-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f2a41-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2a41-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a41-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="f2a41-106">podczas Maksymalna liczba bajtów w `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f2a41-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="f2a41-107">określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="f2a41-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="f2a41-108">określoną Wskaźnik do tablicy bajtów zawierającej token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f2a41-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a41-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2a41-109">Remarks</span></span>  
 <span data-ttu-id="f2a41-110">Token klucza publicznego zestawu to ostatnie osiem bajtów skrótu SHA1 klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f2a41-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2a41-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f2a41-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a41-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2a41-112">Requirements</span></span>  
 <span data-ttu-id="f2a41-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a41-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a41-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2a41-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2a41-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2a41-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a41-116">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a41-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a41-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2a41-117">See also</span></span>

- [<span data-ttu-id="f2a41-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2a41-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="f2a41-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f2a41-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
