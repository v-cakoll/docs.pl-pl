---
title: ICLRDataTarget2::FreeVirtual — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02bba59a1c4445b3e432d5e44f2bccc4b72ce1da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711658"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="44c19-102">ICLRDataTarget2::FreeVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="44c19-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="44c19-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych w celu zwolnienia pamięci, która była przydzielona wcześniej w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="44c19-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44c19-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44c19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44c19-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="44c19-106">[in] A `CLRDATA_ADDRESS` wartość, która określa początkowy adres pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="44c19-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="44c19-107">[in] Rozmiar w bajtach, pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="44c19-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="44c19-108">[in] Flagi sterujące zwalnianie pamięci.</span><span class="sxs-lookup"><span data-stu-id="44c19-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="44c19-109">Zobacz Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="44c19-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44c19-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44c19-110">Remarks</span></span>  
 <span data-ttu-id="44c19-111">`FreeVirtual` Metody służy jako logiczne otoki dla Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="44c19-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="44c19-112">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="44c19-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44c19-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44c19-113">Requirements</span></span>  
 <span data-ttu-id="44c19-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44c19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44c19-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="44c19-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="44c19-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44c19-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44c19-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44c19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c19-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44c19-118">See also</span></span>
- [<span data-ttu-id="44c19-119">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="44c19-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="44c19-120">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="44c19-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
