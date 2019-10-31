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
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131369"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="73ee4-102">ICorDebugRegisterSet2::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="73ee4-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="73ee4-103">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="73ee4-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ee4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73ee4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73ee4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73ee4-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="73ee4-106">podczas Rozmiar tablicy `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="73ee4-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="73ee4-107">określoną Tablica bajtów, z których każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="73ee4-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="73ee4-108">Jeśli rejestr jest dostępny, zostanie ustawiony odpowiedni bit rejestru.</span><span class="sxs-lookup"><span data-stu-id="73ee4-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73ee4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73ee4-109">Remarks</span></span>  
 <span data-ttu-id="73ee4-110">Wartości wyliczenia CorDebugRegister — określają rejestry różnych mikroprocesorów.</span><span class="sxs-lookup"><span data-stu-id="73ee4-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="73ee4-111">Górne pięć bitów każdej wartości jest indeksem do `availableRegChunks` tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="73ee4-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="73ee4-112">Mniejsze trzy bity każdej wartości określają pozycję bitową w ramach indeksowanego bajtu.</span><span class="sxs-lookup"><span data-stu-id="73ee4-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="73ee4-113">Uwzględniając `CorDebugRegister` wartość określającą konkretny rejestr, pozycja rejestru w masce jest określana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="73ee4-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="73ee4-114">Wyodrębnij indeks wymagany do uzyskania dostępu do poprawnego bajtu w tablicy `availableRegChunks`:</span><span class="sxs-lookup"><span data-stu-id="73ee4-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="73ee4-115">`CorDebugRegister` wartość > > 3</span><span class="sxs-lookup"><span data-stu-id="73ee4-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="73ee4-116">Wyodrębnij pozycję bitową w zaindeksowanym bajcie, gdzie bit zero jest najmniej znaczącym bitem:</span><span class="sxs-lookup"><span data-stu-id="73ee4-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="73ee4-117">`CorDebugRegister` wartość & 7</span><span class="sxs-lookup"><span data-stu-id="73ee4-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73ee4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73ee4-118">Requirements</span></span>  
 <span data-ttu-id="73ee4-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73ee4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73ee4-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73ee4-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73ee4-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73ee4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73ee4-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73ee4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ee4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73ee4-123">See also</span></span>

- [<span data-ttu-id="73ee4-124">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="73ee4-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="73ee4-125">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="73ee4-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
