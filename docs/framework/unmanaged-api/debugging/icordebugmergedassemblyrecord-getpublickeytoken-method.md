---
title: 'ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 4cd0ff788401a7b5d70e215209194c0eb6cad1f8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212116"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="85636-102">ICorDebugMergedAssemblyRecord:: GetPublicKeyToken —, Metoda</span><span class="sxs-lookup"><span data-stu-id="85636-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="85636-103">Pobiera token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="85636-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85636-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85636-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85636-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85636-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="85636-106">podczas Maksymalna liczba bajtów w `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="85636-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="85636-107">określoną Wskaźnik do rzeczywistej liczby bajtów zapisanych do `pbPublicKeyToken` tablicy.</span><span class="sxs-lookup"><span data-stu-id="85636-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="85636-108">określoną Wskaźnik do tablicy bajtów zawierającej token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="85636-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85636-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85636-109">Remarks</span></span>  
 <span data-ttu-id="85636-110">Token klucza publicznego zestawu to ostatnie osiem bajtów skrótu SHA1 klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="85636-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85636-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="85636-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85636-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85636-112">Requirements</span></span>  
 <span data-ttu-id="85636-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85636-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85636-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85636-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85636-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85636-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85636-116">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85636-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85636-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85636-117">See also</span></span>

- [<span data-ttu-id="85636-118">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="85636-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="85636-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="85636-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
