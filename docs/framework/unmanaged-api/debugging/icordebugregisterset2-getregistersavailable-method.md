---
title: ICorDebugRegisterSet2::GetRegistersAvailable — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1522d643a69c47eec03770a8f51756dd4250075a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309423"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="10191-102">ICorDebugRegisterSet2::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="10191-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="10191-103">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrach.</span><span class="sxs-lookup"><span data-stu-id="10191-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10191-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10191-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10191-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10191-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="10191-106">[in] Rozmiar `availableRegChunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="10191-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="10191-107">[out] Tablica bajtów, każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="10191-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="10191-108">Jeśli rejestr jest dostępny, odpowiadający mu bit rejestru jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="10191-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10191-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10191-109">Remarks</span></span>  
 <span data-ttu-id="10191-110">Wartości wyliczenia cordebugregister — Określ rejestrów mikroprocesory różne.</span><span class="sxs-lookup"><span data-stu-id="10191-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="10191-111">Górny pięć bitów każdej wartości są Indeksuj do `availableRegChunks` tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="10191-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="10191-112">Niższe trzy usługi bits w każdej wartości identyfikują Pozycja bitu w indeksowanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="10191-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="10191-113">Biorąc pod uwagę `CorDebugRegister` wartość, która określa określonego rejestru, pozycji Zarejestruj maski jest określany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="10191-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="10191-114">Wyodrębnij indeksu umożliwiającymi dostęp poprawne bajtów w `availableRegChunks` tablicy:</span><span class="sxs-lookup"><span data-stu-id="10191-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     `CorDebugRegister` <span data-ttu-id="10191-115">wartość >> 3</span><span class="sxs-lookup"><span data-stu-id="10191-115">value >> 3</span></span>  
  
2. <span data-ttu-id="10191-116">Wyodrębnij Pozycja bitu w indeksowanych bajtów, gdzie bit zero jest najmniej znaczący bit:</span><span class="sxs-lookup"><span data-stu-id="10191-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     `CorDebugRegister` <span data-ttu-id="10191-117">Wartość & 7</span><span class="sxs-lookup"><span data-stu-id="10191-117">value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10191-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10191-118">Requirements</span></span>  
 <span data-ttu-id="10191-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10191-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10191-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10191-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10191-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10191-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="10191-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="10191-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="10191-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10191-123">See also</span></span>

- [<span data-ttu-id="10191-124">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="10191-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="10191-125">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="10191-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
