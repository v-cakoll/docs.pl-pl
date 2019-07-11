---
title: ICorDebugRegisterSet2::GetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1b90390689e709ee131935bd6417fa6b273eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769980"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="82e7e-102">ICorDebugRegisterSet2::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="82e7e-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="82e7e-103">Pobiera wartość każdego rejestru (dla platformy, na którym aktualnie wykonuje kod) określonej przez dany bitowej maski.</span><span class="sxs-lookup"><span data-stu-id="82e7e-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82e7e-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="82e7e-106">[in] Rozmiar w bajtach z `mask` tablicy.</span><span class="sxs-lookup"><span data-stu-id="82e7e-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="82e7e-107">[in] Tablica bajtów, każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="82e7e-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="82e7e-108">Jeśli bit ma wartość 1, zostanie pobrana wartość w odpowiednim rejestrze.</span><span class="sxs-lookup"><span data-stu-id="82e7e-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="82e7e-109">[in] Liczba wartości rejestru, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="82e7e-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="82e7e-110">[out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="82e7e-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82e7e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82e7e-111">Remarks</span></span>  
 <span data-ttu-id="82e7e-112">`GetRegisters` Metoda zwraca tablicę wartości z rejestrów, określonych przez maskę.</span><span class="sxs-lookup"><span data-stu-id="82e7e-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="82e7e-113">Tablica nie zawiera wartości rejestrów, w których bit maski nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="82e7e-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="82e7e-114">Dlatego rozmiar `regBuffer` tablicy musi być równa liczbie 1 maski.</span><span class="sxs-lookup"><span data-stu-id="82e7e-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="82e7e-115">Jeśli wartość `regCount` jest zbyt mały dla liczby rejestrów wskazywanym przez maskę wartości wyższej rejestrów numerowane zostanie obcięta z zestawu.</span><span class="sxs-lookup"><span data-stu-id="82e7e-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="82e7e-116">Jeśli `regCount` jest zbyt duży, nieużywane `regBuffer` elementy zostaną zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="82e7e-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="82e7e-117">Jeśli rejestrowanie niedostępne jest wskazywany przez maskę, nieokreślona wartość zwracaną dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="82e7e-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="82e7e-118">`ICorDebugRegisterSet2::GetRegisters` Metoda jest niezbędna dla platform, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="82e7e-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="82e7e-119">Na przykład IA64 ma 128 rejestrów ogólnego przeznaczenia i 128 rejestrów zmiennoprzecinkowych, dlatego potrzebujesz więcej niż 64-bitowej maski bitowej.</span><span class="sxs-lookup"><span data-stu-id="82e7e-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="82e7e-120">Jeśli nie masz więcej niż 64 rejestry, tak jak w przypadku na platformach takich jak x86, `GetRegisters` metody w rzeczywistości po prostu tłumaczy bajtów w `mask` tablicy typu byte do `ULONG64` , a następnie wywołuje [ICorDebugRegisterSet:: Getregisters —](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metody, która przyjmuje `ULONG64` maski.</span><span class="sxs-lookup"><span data-stu-id="82e7e-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e7e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82e7e-121">Requirements</span></span>  
 <span data-ttu-id="82e7e-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e7e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e7e-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82e7e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82e7e-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82e7e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82e7e-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e7e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e7e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82e7e-126">See also</span></span>

- [<span data-ttu-id="82e7e-127">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="82e7e-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="82e7e-128">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="82e7e-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
