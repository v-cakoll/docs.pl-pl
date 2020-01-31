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
ms.openlocfilehash: 54a5fb50a0177fe9886582c112f16ce871ea9df4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792061"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="2079b-102">ICorDebugRegisterSet2::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="2079b-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="2079b-103">Pobiera wartość każdego rejestru (dla platformy, w której kod jest aktualnie wykonywany), która jest określona przez daną maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="2079b-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2079b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2079b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2079b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2079b-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="2079b-106">podczas Rozmiar (w bajtach) tablicy `mask`.</span><span class="sxs-lookup"><span data-stu-id="2079b-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="2079b-107">podczas Tablica bajtów, z których każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="2079b-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="2079b-108">Jeśli bit wynosi 1, zostanie pobrana odpowiednia wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="2079b-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="2079b-109">podczas Liczba wartości rejestru do pobrania.</span><span class="sxs-lookup"><span data-stu-id="2079b-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="2079b-110">określoną Tablica obiektów `CORDB_REGISTER`, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="2079b-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2079b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2079b-111">Remarks</span></span>  
 <span data-ttu-id="2079b-112">Metoda `GetRegisters` zwraca tablicę wartości z rejestrów, które są określone przez maskę.</span><span class="sxs-lookup"><span data-stu-id="2079b-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="2079b-113">Tablica nie zawiera wartości rejestrów, których bit maski nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="2079b-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="2079b-114">W ten sposób rozmiar tablicy `regBuffer` musi być równy liczbie 1 w masce.</span><span class="sxs-lookup"><span data-stu-id="2079b-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="2079b-115">Jeśli wartość `regCount` jest za mała dla liczby rejestrów wskazywanych przez maskę, wartości wyższych numerowanych rejestrów zostaną obcięte z zestawu.</span><span class="sxs-lookup"><span data-stu-id="2079b-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="2079b-116">Jeśli `regCount` jest zbyt duży, nieużywane elementy `regBuffer` będą niemodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="2079b-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="2079b-117">Jeśli niedostępna Rejestracja jest wskazywana przez maskę, zostanie zwrócona wartość nieokreślona dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="2079b-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="2079b-118">Metoda `ICorDebugRegisterSet2::GetRegisters` jest niezbędna dla platform, które mają więcej niż 64 rejestrów.</span><span class="sxs-lookup"><span data-stu-id="2079b-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="2079b-119">Na przykład IA64 ma 128 rejestry ogólnego przeznaczenia i 128 rejestry zmiennoprzecinkowe, więc potrzebujesz więcej niż 64-bitów w masce bitowej.</span><span class="sxs-lookup"><span data-stu-id="2079b-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="2079b-120">Jeśli nie ma więcej niż 64 rejestrów, tak jak w przypadku platform, takich jak x86, Metoda `GetRegisters` faktycznie tłumaczy bajty w tablicy `mask` bajtów na `ULONG64`, a następnie wywołuje metodę [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , która przyjmuje maskę `ULONG64`.</span><span class="sxs-lookup"><span data-stu-id="2079b-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2079b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2079b-121">Requirements</span></span>  
 <span data-ttu-id="2079b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2079b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2079b-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2079b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2079b-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2079b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2079b-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2079b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2079b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2079b-126">See also</span></span>

- [<span data-ttu-id="2079b-127">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2079b-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="2079b-128">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="2079b-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
