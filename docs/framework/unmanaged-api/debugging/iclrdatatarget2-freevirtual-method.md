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
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793656"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="d8eea-102">ICLRDataTarget2::FreeVirtual — Metoda</span><span class="sxs-lookup"><span data-stu-id="d8eea-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="d8eea-103">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) do wolnej pamięci, która została wcześniej przydzielone w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d8eea-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8eea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8eea-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8eea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8eea-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="d8eea-106">podczas Wartość `CLRDATA_ADDRESS`, która określa początkowy adres pamięci, która ma zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="d8eea-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="d8eea-107">podczas Rozmiar (w bajtach) pamięci, która ma zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="d8eea-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="d8eea-108">podczas Flagi kontrolujące zwalnianie pamięci.</span><span class="sxs-lookup"><span data-stu-id="d8eea-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="d8eea-109">Zobacz funkcję Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="d8eea-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8eea-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8eea-110">Remarks</span></span>  
 <span data-ttu-id="d8eea-111">Metoda `FreeVirtual` służy jako otoka logiczna dla funkcji Win32 `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="d8eea-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="d8eea-112">Ta metoda jest implementowana przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8eea-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8eea-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d8eea-113">Requirements</span></span>  
 <span data-ttu-id="d8eea-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8eea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8eea-115">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d8eea-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d8eea-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d8eea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8eea-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8eea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8eea-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8eea-118">See also</span></span>

- [<span data-ttu-id="d8eea-119">ICLRDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d8eea-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="d8eea-120">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="d8eea-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
