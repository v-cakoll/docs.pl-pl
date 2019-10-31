---
title: ICLRDataTarget::GetMachineType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 941d1b4057ef78a6235a0ba853e48a000f2087e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122889"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="5bafd-102">ICLRDataTarget::GetMachineType — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bafd-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="5bafd-103">Pobiera identyfikator rodzaju instrukcji, która jest używana przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="5bafd-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bafd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bafd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bafd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bafd-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="5bafd-106">określoną Wskaźnik do wartości, która wskazuje zestaw instrukcji używany przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="5bafd-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="5bafd-107">Zwrócony `machineType` jest jednym ze stałych IMAGE_FILE_MACHINE, które są zdefiniowane w pliku nagłówkowym WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="5bafd-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bafd-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bafd-108">Requirements</span></span>  
 <span data-ttu-id="5bafd-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bafd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bafd-110">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5bafd-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5bafd-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5bafd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bafd-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bafd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bafd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bafd-113">See also</span></span>

- [<span data-ttu-id="5bafd-114">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bafd-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
