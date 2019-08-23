---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e08b1edcef3e93caa82be3a4342c6a0264734bea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940021"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="0a0e1-102">ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda</span><span class="sxs-lookup"><span data-stu-id="0a0e1-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="0a0e1-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a0e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a0e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a0e1-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="0a0e1-106">podczas Maksymalna liczba bajtów w `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="0a0e1-107">określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do `pbPublicKey` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="0a0e1-108">określoną Wskaźnik do tablicy bajtów zawierającej klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a0e1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a0e1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a0e1-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0a0e1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0e1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a0e1-111">Requirements</span></span>  
 <span data-ttu-id="0a0e1-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a0e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a0e1-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a0e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a0e1-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a0e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a0e1-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a0e1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0e1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a0e1-116">See also</span></span>

- [<span data-ttu-id="0a0e1-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a0e1-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="0a0e1-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a0e1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
