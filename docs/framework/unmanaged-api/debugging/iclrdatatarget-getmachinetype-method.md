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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff9c88d534e0bfe51075a76581af37aba791a3da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698255"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="4bf90-102">ICLRDataTarget::GetMachineType — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bf90-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="4bf90-103">Pobiera identyfikator dla rodzaju — zestaw instrukcji używanej przez proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="4bf90-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bf90-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bf90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bf90-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="4bf90-106">[out] Wskaźnik do wartości, który wskazuje, że instrukcji zestawu, który proces docelowy korzysta.</span><span class="sxs-lookup"><span data-stu-id="4bf90-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="4bf90-107">Zwrócony `machineType` jest jednym ze stałych IMAGE_FILE_MACHINE, które są zdefiniowane w pliku nagłówkowym opis pliku WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="4bf90-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf90-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bf90-108">Requirements</span></span>  
 <span data-ttu-id="4bf90-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf90-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf90-110">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4bf90-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4bf90-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bf90-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bf90-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf90-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf90-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bf90-113">See also</span></span>

- [<span data-ttu-id="4bf90-114">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="4bf90-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
