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
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379153"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="017cc-102">ICorDebugRegisterSet::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="017cc-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="017cc-103">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod), który jest określony przez maskę bitową.</span><span class="sxs-lookup"><span data-stu-id="017cc-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="017cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="017cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="017cc-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="017cc-106">podczas Maska bitów określająca, które wartości rejestru mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="017cc-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="017cc-107">Każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="017cc-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="017cc-108">Jeśli bit jest ustawiony na jeden, zostanie pobrana wartość rejestru. w przeciwnym razie wartość rejestru nie zostanie pobrana.</span><span class="sxs-lookup"><span data-stu-id="017cc-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="017cc-109">podczas Liczba wartości rejestru do pobrania.</span><span class="sxs-lookup"><span data-stu-id="017cc-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="017cc-110">określoną Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="017cc-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="017cc-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="017cc-111">Remarks</span></span>  
 <span data-ttu-id="017cc-112">Rozmiar tablicy musi być równy liczbie bitów ustawionych dla jednej w masce bitów.</span><span class="sxs-lookup"><span data-stu-id="017cc-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="017cc-113">`regCount`Parametr określa liczbę elementów w buforze, które będą otrzymywać wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="017cc-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="017cc-114">Jeśli `regCount` wartość jest za mała dla liczby rejestrów wskazanych przez maskę, te rejestry o wyższych numerach zostaną obcięte z zestawu.</span><span class="sxs-lookup"><span data-stu-id="017cc-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="017cc-115">Jeśli `regCount` wartość jest zbyt duża, nieużywane `regBuffer` elementy będą niemodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="017cc-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="017cc-116">Jeśli Maska bitów określa rejestr, który jest niedostępny, `GetRegisters` zwraca wartość nieokreśloną dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="017cc-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017cc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="017cc-117">Requirements</span></span>  
 <span data-ttu-id="017cc-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="017cc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017cc-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="017cc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="017cc-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="017cc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="017cc-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017cc-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="017cc-122">See also</span></span>

- [<span data-ttu-id="017cc-123">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="017cc-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="017cc-124">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="017cc-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
