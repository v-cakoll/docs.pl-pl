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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378219"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="0c73a-102">ICorDebugRegisterSet2::GetRegistersAvailable — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c73a-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="0c73a-103">Pobiera tablicę bajtów, która zawiera mapę bitową dostępnych rejestrów.</span><span class="sxs-lookup"><span data-stu-id="0c73a-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c73a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c73a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c73a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c73a-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="0c73a-106">podczas Rozmiar `availableRegChunks` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0c73a-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="0c73a-107">określoną Tablica bajtów, z których każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="0c73a-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="0c73a-108">Jeśli rejestr jest dostępny, zostanie ustawiony odpowiedni bit rejestru.</span><span class="sxs-lookup"><span data-stu-id="0c73a-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c73a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c73a-109">Remarks</span></span>  
 <span data-ttu-id="0c73a-110">Wartości wyliczenia CorDebugRegister — określają rejestry różnych mikroprocesorów.</span><span class="sxs-lookup"><span data-stu-id="0c73a-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="0c73a-111">Górne pięć bitów każdej wartości jest indeksem w `availableRegChunks` tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="0c73a-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="0c73a-112">Mniejsze trzy bity każdej wartości określają pozycję bitową w ramach indeksowanego bajtu.</span><span class="sxs-lookup"><span data-stu-id="0c73a-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="0c73a-113">Uwzględniając wartość określającą `CorDebugRegister` konkretny rejestr, pozycja rejestru w masce jest określana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0c73a-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="0c73a-114">Wyodrębnij indeks wymagany do uzyskania dostępu do poprawnego bajtu w `availableRegChunks` tablicy:</span><span class="sxs-lookup"><span data-stu-id="0c73a-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="0c73a-115">`CorDebugRegister`wartość >> 3</span><span class="sxs-lookup"><span data-stu-id="0c73a-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="0c73a-116">Wyodrębnij pozycję bitową w zaindeksowanym bajcie, gdzie bit zero jest najmniej znaczącym bitem:</span><span class="sxs-lookup"><span data-stu-id="0c73a-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="0c73a-117">`CorDebugRegister`wartość & 7</span><span class="sxs-lookup"><span data-stu-id="0c73a-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c73a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c73a-118">Requirements</span></span>  
 <span data-ttu-id="0c73a-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c73a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c73a-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c73a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c73a-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c73a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c73a-122">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c73a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c73a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c73a-123">See also</span></span>

- [<span data-ttu-id="0c73a-124">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c73a-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="0c73a-125">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c73a-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
