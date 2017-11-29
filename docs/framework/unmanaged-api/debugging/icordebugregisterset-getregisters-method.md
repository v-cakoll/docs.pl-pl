---
title: "ICorDebugRegisterSet::GetRegisters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7edae3d3be1bcfb80b7a1e432fd5f25e119f078f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="49d48-102">ICorDebugRegisterSet::GetRegisters — Metoda</span><span class="sxs-lookup"><span data-stu-id="49d48-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="49d48-103">Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kodu) określonym przez maska bitowa.</span><span class="sxs-lookup"><span data-stu-id="49d48-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49d48-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49d48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49d48-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="49d48-106">[in] Maska bitowa, która określa rejestru, które mają być pobierane wartości.</span><span class="sxs-lookup"><span data-stu-id="49d48-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="49d48-107">Każdy bit odpowiada rejestru.</span><span class="sxs-lookup"><span data-stu-id="49d48-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="49d48-108">Jeśli bit ma wartość 1, wartość rejestru jest pobierana; w przeciwnym razie wartość rejestru nie została pobrana.</span><span class="sxs-lookup"><span data-stu-id="49d48-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="49d48-109">[in] Liczba wartości rejestru, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="49d48-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="49d48-110">[out] Tablica `CORDB_REGISTER` obiektów, z których każdy odbiera wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="49d48-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49d48-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49d48-111">Remarks</span></span>  
 <span data-ttu-id="49d48-112">Rozmiar tablicy powinna być równa Liczba bitów w maska bitowa.</span><span class="sxs-lookup"><span data-stu-id="49d48-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="49d48-113">`regCount` Parametr określa liczbę elementów w buforze, który będzie otrzymywał wartości rejestru.</span><span class="sxs-lookup"><span data-stu-id="49d48-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="49d48-114">Jeśli `regCount` wartość jest za mały dla liczby rejestrów wskazywanym przez maski, wyższy rejestrów numerowane zostanie obcięty z zestawu.</span><span class="sxs-lookup"><span data-stu-id="49d48-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="49d48-115">Jeśli `regCount` wartość jest zbyt duża, nieużywane `regBuffer` elementy zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="49d48-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="49d48-116">Jeśli maska bitowa określa rejestru, który jest niedostępny, `GetRegisters` zwraca nieokreśloną wartość rejestru.</span><span class="sxs-lookup"><span data-stu-id="49d48-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d48-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49d48-117">Requirements</span></span>  
 <span data-ttu-id="49d48-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49d48-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d48-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49d48-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49d48-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49d48-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49d48-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d48-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d48-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49d48-122">See Also</span></span>  
 [<span data-ttu-id="49d48-123">ICorDebugRegisterSet — interfejs</span><span class="sxs-lookup"><span data-stu-id="49d48-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="49d48-124">ICorDebugRegisterSet2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="49d48-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
