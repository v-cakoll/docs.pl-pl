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
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181405"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="19172-102">ICLRDataTarget2::FreeVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="19172-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="19172-103">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych w celu zwolnienia pamięci, która była przydzielona wcześniej w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="19172-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19172-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19172-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19172-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19172-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="19172-106">[in] A `CLRDATA_ADDRESS` wartość, która określa początkowy adres pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="19172-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="19172-107">[in] Rozmiar w bajtach, pamięci, który ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="19172-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="19172-108">[in] Flagi sterujące zwalnianie pamięci.</span><span class="sxs-lookup"><span data-stu-id="19172-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="19172-109">Zobacz Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="19172-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19172-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19172-110">Remarks</span></span>  
 <span data-ttu-id="19172-111">`FreeVirtual` Metody służy jako logiczne otoki dla Win32 `VirtualFree` funkcji.</span><span class="sxs-lookup"><span data-stu-id="19172-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="19172-112">Ta metoda jest implementowana przez moduł zapisujący debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19172-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19172-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19172-113">Requirements</span></span>  
 <span data-ttu-id="19172-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19172-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19172-115">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="19172-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="19172-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19172-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="19172-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="19172-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="19172-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19172-118">See also</span></span>

- [<span data-ttu-id="19172-119">ICLRDataTarget2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19172-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="19172-120">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="19172-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
