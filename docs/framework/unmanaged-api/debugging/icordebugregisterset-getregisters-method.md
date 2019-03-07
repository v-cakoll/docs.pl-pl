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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4887d44f0ac5603280efa0abdbd7e65c71fc3ca
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485459"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="425c7-102">ICorDebugRegisterSet::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="425c7-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="425c7-103">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.</span><span class="sxs-lookup"><span data-stu-id="425c7-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="425c7-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="425c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="425c7-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="425c7-106">[in] Maska bitów, określający które rejestr wartości, które mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="425c7-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="425c7-107">Każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="425c7-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="425c7-108">Jeśli bit jest ustawiony na jedną, wartość rejestru jest pobierana; w przeciwnym razie wartości rejestru nie są pobierane.</span><span class="sxs-lookup"><span data-stu-id="425c7-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="425c7-109">[in] Liczba wartości rejestru, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="425c7-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="425c7-110">[out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="425c7-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="425c7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="425c7-111">Remarks</span></span>  
 <span data-ttu-id="425c7-112">Rozmiar tablicy powinna być równa liczbie bitów w masce bitowej.</span><span class="sxs-lookup"><span data-stu-id="425c7-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="425c7-113">`regCount` Parametr określa liczbę elementów w buforze, który będzie otrzymywał wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="425c7-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="425c7-114">Jeśli `regCount` wartość jest zbyt mały dla liczby rejestrów wskazywanym przez maskę, wyższe rejestrów numerowane zostanie obcięta z zestawu.</span><span class="sxs-lookup"><span data-stu-id="425c7-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="425c7-115">Jeśli `regCount` jest zbyt duża, nieużywane `regBuffer` elementy zostaną zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="425c7-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="425c7-116">Jeśli maska bitowa, określa rejestru, który jest niedostępny, `GetRegisters` zwraca wartość nieokreśloną dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="425c7-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425c7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="425c7-117">Requirements</span></span>  
 <span data-ttu-id="425c7-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="425c7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="425c7-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="425c7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="425c7-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="425c7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="425c7-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="425c7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425c7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="425c7-122">See also</span></span>
- [<span data-ttu-id="425c7-123">ICorDebugRegisterSet, interfejs</span><span class="sxs-lookup"><span data-stu-id="425c7-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="425c7-124">ICorDebugRegisterSet2, interfejs</span><span class="sxs-lookup"><span data-stu-id="425c7-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
