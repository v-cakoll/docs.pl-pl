---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793118"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="45e25-102">ICorDebugMergedAssemblyRecord:: GetPublicKey, Metoda</span><span class="sxs-lookup"><span data-stu-id="45e25-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="45e25-103">Pobiera klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="45e25-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45e25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45e25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45e25-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="45e25-106">podczas Maksymalna liczba bajtów w tablicy `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="45e25-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="45e25-107">określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do tablicy `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="45e25-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="45e25-108">określoną Wskaźnik do tablicy bajtów zawierającej klucz publiczny zestawu.</span><span class="sxs-lookup"><span data-stu-id="45e25-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e25-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45e25-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45e25-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="45e25-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e25-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45e25-111">Requirements</span></span>  
 <span data-ttu-id="45e25-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e25-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e25-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45e25-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45e25-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="45e25-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e25-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e25-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e25-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45e25-116">See also</span></span>

- [<span data-ttu-id="45e25-117">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="45e25-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="45e25-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45e25-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
