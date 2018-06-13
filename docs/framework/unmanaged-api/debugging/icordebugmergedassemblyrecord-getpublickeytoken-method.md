---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken — metoda
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b70118d77deb7ad6879ed4bd48b1cd37122820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414011"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="7332a-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken — metoda</span><span class="sxs-lookup"><span data-stu-id="7332a-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="7332a-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7332a-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7332a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7332a-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7332a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7332a-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="7332a-106">[in] Maksymalna liczba bajtów w `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7332a-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="7332a-107">[out] Wskaźnik do rzeczywista liczba bajtów zapisanych na `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7332a-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="7332a-108">[out] Wskaźnik do tablicy typu byte, który zawiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7332a-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7332a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7332a-109">Remarks</span></span>  
 <span data-ttu-id="7332a-110">Token klucza publicznego zestawu jest ostatnich ośmiu bajtów skrótu SHA1 jego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="7332a-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7332a-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7332a-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7332a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7332a-112">Requirements</span></span>  
 <span data-ttu-id="7332a-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7332a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7332a-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7332a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7332a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7332a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7332a-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7332a-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7332a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7332a-117">See Also</span></span>  
 [<span data-ttu-id="7332a-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="7332a-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="7332a-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7332a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
