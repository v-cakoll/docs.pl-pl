---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 95ed1303b33b328d1f14ecea6cc318e14991cd54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129787"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="0d008-102">ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda</span><span class="sxs-lookup"><span data-stu-id="0d008-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="0d008-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0d008-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d008-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d008-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d008-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d008-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="0d008-106">podczas Maksymalna liczba bajtów w tablicy `pbPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="0d008-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="0d008-107">określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do tablicy `pbPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="0d008-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="0d008-108">określoną Wskaźnik do tablicy bajtów zawierającej token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0d008-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d008-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d008-109">Remarks</span></span>  
 <span data-ttu-id="0d008-110">Token klucza publicznego zestawu to ostatnie osiem bajtów skrótu SHA1 klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0d008-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d008-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0d008-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d008-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d008-112">Requirements</span></span>  
 <span data-ttu-id="0d008-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d008-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d008-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d008-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d008-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d008-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d008-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d008-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d008-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d008-117">See also</span></span>

- [<span data-ttu-id="0d008-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d008-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="0d008-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0d008-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
