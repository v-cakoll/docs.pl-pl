---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178723"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="be886-102">ICorDebugMergedAssemblyRecord::Metoda GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="be886-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="be886-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="be886-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be886-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be886-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be886-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be886-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="be886-106">[w] Maksymalna liczba bajtów `pbPublicKeyToken` w tablicy.</span><span class="sxs-lookup"><span data-stu-id="be886-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="be886-107">[na zewnątrz] Wskaźnik do rzeczywistej liczby bajtów `pbPublicKeyToken` zapisanych w tablicy.</span><span class="sxs-lookup"><span data-stu-id="be886-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="be886-108">[na zewnątrz] Wskaźnik do tablicy bajtów, która zawiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="be886-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be886-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be886-109">Remarks</span></span>  
 <span data-ttu-id="be886-110">Token klucza publicznego zestawu jest ostatnich ośmiu bajtów skrótu SHA1 jego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="be886-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be886-111">Ta metoda jest dostępna tylko w przypadku platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="be886-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be886-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be886-112">Requirements</span></span>  
 <span data-ttu-id="be886-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be886-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be886-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be886-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be886-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be886-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be886-116">**Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be886-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be886-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be886-117">See also</span></span>

- [<span data-ttu-id="be886-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="be886-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="be886-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="be886-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
