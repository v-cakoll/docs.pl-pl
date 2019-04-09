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
ms.openlocfilehash: b417685361126951470571e2440cc842ab1c94fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153910"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="b1984-102">ICorDebugRegisterSet::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1984-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="b1984-103">Pobiera wartość każdego rejestru (na komputerze, który aktualnie wykonuje kod) określonej przez Maska bitów.</span><span class="sxs-lookup"><span data-stu-id="b1984-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1984-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1984-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1984-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1984-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="b1984-106">[in] Maska bitów, określający które rejestr wartości, które mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="b1984-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="b1984-107">Każdy bit odnosi się do rejestru.</span><span class="sxs-lookup"><span data-stu-id="b1984-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="b1984-108">Jeśli bit jest ustawiony na jedną, wartość rejestru jest pobierana; w przeciwnym razie wartości rejestru nie są pobierane.</span><span class="sxs-lookup"><span data-stu-id="b1984-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="b1984-109">[in] Liczba wartości rejestru, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b1984-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="b1984-110">[out] Tablica `CORDB_REGISTER` obiektów, z których każdy otrzymuje wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="b1984-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1984-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1984-111">Remarks</span></span>  
 <span data-ttu-id="b1984-112">Rozmiar tablicy powinna być równa liczbie bitów w masce bitowej.</span><span class="sxs-lookup"><span data-stu-id="b1984-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="b1984-113">`regCount` Parametr określa liczbę elementów w buforze, który będzie otrzymywał wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="b1984-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="b1984-114">Jeśli `regCount` wartość jest zbyt mały dla liczby rejestrów wskazywanym przez maskę, wyższe rejestrów numerowane zostanie obcięta z zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1984-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="b1984-115">Jeśli `regCount` jest zbyt duża, nieużywane `regBuffer` elementy zostaną zostały zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b1984-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="b1984-116">Jeśli maska bitowa, określa rejestru, który jest niedostępny, `GetRegisters` zwraca wartość nieokreśloną dla tego rejestru.</span><span class="sxs-lookup"><span data-stu-id="b1984-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1984-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1984-117">Requirements</span></span>  
 <span data-ttu-id="b1984-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1984-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1984-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1984-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1984-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1984-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b1984-121">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b1984-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1984-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1984-122">See also</span></span>

- [<span data-ttu-id="b1984-123">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1984-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="b1984-124">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1984-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
