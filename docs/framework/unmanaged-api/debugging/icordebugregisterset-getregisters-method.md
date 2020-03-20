---
title: ICorDebugRegisterSet::GetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178543"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="6d652-102">ICorDebugRegisterSet::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d652-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="6d652-103">Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="6d652-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d652-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d652-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d652-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d652-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="6d652-106">[w] Maska bitowa określająca, które wartości rejestru mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="6d652-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="6d652-107">Każdy bit odpowiada rejestrowi.</span><span class="sxs-lookup"><span data-stu-id="6d652-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="6d652-108">Jeśli bit jest ustawiony na jeden, wartość rejestru jest pobierana; w przeciwnym razie wartość rejestru nie jest pobierana.</span><span class="sxs-lookup"><span data-stu-id="6d652-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="6d652-109">[w] Liczba wartości rejestru do pobrania.</span><span class="sxs-lookup"><span data-stu-id="6d652-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="6d652-110">[na zewnątrz] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="6d652-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d652-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d652-111">Remarks</span></span>  
 <span data-ttu-id="6d652-112">Rozmiar tablicy powinien być równy liczbie bitów ustawionych na jeden w masce bitowej.</span><span class="sxs-lookup"><span data-stu-id="6d652-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="6d652-113">Parametr `regCount` określa liczbę elementów w buforze, które otrzymają wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="6d652-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="6d652-114">Jeśli `regCount` wartość jest zbyt mała dla liczby rejestrów wskazanych przez maskę, wyższe numerowane rejestry zostaną obcięty z zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d652-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="6d652-115">Jeśli `regCount` wartość jest zbyt duża, `regBuffer` nieużywane elementy będą niezmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="6d652-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="6d652-116">Jeśli maska bitowa określa rejestr, `GetRegisters` który jest niedostępny, zwraca nieokreśloną wartość dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="6d652-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d652-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d652-117">Requirements</span></span>  
 <span data-ttu-id="6d652-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d652-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d652-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d652-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d652-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d652-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d652-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d652-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d652-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d652-122">See also</span></span>

- [<span data-ttu-id="6d652-123">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6d652-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="6d652-124">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6d652-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
