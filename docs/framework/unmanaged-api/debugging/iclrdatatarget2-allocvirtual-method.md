---
title: ICLRDataTarget2::AllocVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e63b6a015bd1ffa86d8fd04b0154dbade85a35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465923"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="aa6cf-102">ICLRDataTarget2::AllocVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa6cf-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="aa6cf-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych można przydzielić pamięci w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa6cf-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa6cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa6cf-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="aa6cf-106">[in] A `CLRDATA_ADDRESS` wartość, która określa żądany adres początkowy pamięci do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="aa6cf-107">[in] Rozmiar w bajtach pamięci do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="aa6cf-108">[in] Flagi sterujące alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="aa6cf-109">Zobacz Win32 `VirtualAlloc` funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="aa6cf-110">[in] Atrybuty ochrony ilość przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="aa6cf-111">Zobacz Win32 `VirtualAlloc` funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="aa6cf-112">[out] Wskaźnik do `CLRDATA_ADDRESS` wartość, która określa adres początkowy rzeczywista ilość przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa6cf-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa6cf-113">Remarks</span></span>  
 <span data-ttu-id="aa6cf-114">`AllocVirtual` Metody służy jako logiczne otoki dla Win32 `VirtualAlloc` funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="aa6cf-115">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa6cf-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa6cf-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa6cf-116">Requirements</span></span>  
 <span data-ttu-id="aa6cf-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa6cf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa6cf-118">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="aa6cf-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="aa6cf-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa6cf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa6cf-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6cf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6cf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa6cf-121">See also</span></span>
- [<span data-ttu-id="aa6cf-122">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa6cf-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="aa6cf-123">FreeVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="aa6cf-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
