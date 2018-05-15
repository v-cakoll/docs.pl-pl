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
ms.openlocfilehash: aca83a66520531074f376a47a7f2994cda237f9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="d741c-102">ICorDebugRegisterSet2::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="d741c-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="d741c-103">Pobiera wartość każdego rejestru (dla platformy, na którym kod jest aktualnie wykonywany) określonym przez dany bitowej maski.</span><span class="sxs-lookup"><span data-stu-id="d741c-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d741c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d741c-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d741c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d741c-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="d741c-106">[in] Rozmiar w bajtach z `mask` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d741c-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="d741c-107">[in] Tablica bajtów, każdy bit odpowiada rejestru.</span><span class="sxs-lookup"><span data-stu-id="d741c-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="d741c-108">Jeśli bit ma wartość 1, będzie można pobrać wartości rejestru odpowiednich.</span><span class="sxs-lookup"><span data-stu-id="d741c-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="d741c-109">[in] Liczba wartości rejestru, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="d741c-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="d741c-110">[out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="d741c-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d741c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d741c-111">Remarks</span></span>  
 <span data-ttu-id="d741c-112">`GetRegisters` Metoda zwraca tablicę wartości z rejestrów, które są określone przez maskę.</span><span class="sxs-lookup"><span data-stu-id="d741c-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="d741c-113">Tablica nie zawiera wartości rejestrów bit maski, których nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="d741c-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="d741c-114">W związku z tym rozmiar `regBuffer` tablicy musi być równa liczbie 1 maski.</span><span class="sxs-lookup"><span data-stu-id="d741c-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="d741c-115">Jeśli wartość `regCount` jest za mały dla liczby rejestrów wskazanych przez maskę wartości wyższej rejestrów numerowane zostanie obcięty z zestawu.</span><span class="sxs-lookup"><span data-stu-id="d741c-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="d741c-116">Jeśli `regCount` jest zbyt duży, nieużywane `regBuffer` elementy zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="d741c-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="d741c-117">Jeśli niedostępny rejestru jest określane przez maski, zostanie zwrócony nieokreśloną wartość do rejestru.</span><span class="sxs-lookup"><span data-stu-id="d741c-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="d741c-118">`ICorDebugRegisterSet2::GetRegisters` Metoda jest niezbędne dla platform, które mają ponad 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="d741c-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="d741c-119">Na przykład IA64 ma 128 rejestrów ogólnego przeznaczenia i 128 rejestrów zmiennoprzecinkowych, więc należy więcej niż 64-bitowej maski bitowej.</span><span class="sxs-lookup"><span data-stu-id="d741c-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="d741c-120">Jeśli nie masz więcej niż 64 rejestrów, tak jak w przypadku na platformach, na przykład x86, `GetRegisters` metody rzeczywista właśnie tłumaczy bajtów w `mask` tablica bajtów do `ULONG64` , a następnie wywołuje [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) metodę, która przyjmuje `ULONG64` maski.</span><span class="sxs-lookup"><span data-stu-id="d741c-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d741c-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d741c-121">Requirements</span></span>  
 <span data-ttu-id="d741c-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d741c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d741c-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d741c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d741c-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d741c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d741c-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d741c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d741c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d741c-126">See Also</span></span>  
 [<span data-ttu-id="d741c-127">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d741c-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [<span data-ttu-id="d741c-128">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="d741c-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
