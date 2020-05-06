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
ms.openlocfilehash: 9d86b23b91702929a86334f557a8d647e19861a4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860588"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="e2300-102">ICLRDataTarget::GetMachineType — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2300-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="e2300-103">Pobiera identyfikator rodzaju instrukcji, która jest używana przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="e2300-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2300-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2300-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2300-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2300-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="e2300-106">określoną Wskaźnik do wartości, która wskazuje zestaw instrukcji używany przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="e2300-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="e2300-107">Zwracana `machineType` jest jedna ze stałych IMAGE_FILE_MACHINE, które są zdefiniowane w pliku nagłówkowym Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="e2300-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2300-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2300-108">Requirements</span></span>  
 <span data-ttu-id="e2300-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2300-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2300-110">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e2300-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e2300-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2300-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2300-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2300-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2300-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2300-113">See also</span></span>

- [<span data-ttu-id="e2300-114">ICLRDataTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e2300-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
