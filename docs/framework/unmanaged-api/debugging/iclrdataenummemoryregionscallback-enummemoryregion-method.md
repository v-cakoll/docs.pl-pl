---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: c8313b7c97eb5d94424259dc91459f62e13368fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785593"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="db5b8-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda</span><span class="sxs-lookup"><span data-stu-id="db5b8-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="db5b8-103">Wywoływane przez [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera, wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="db5b8-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db5b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db5b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db5b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db5b8-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="db5b8-106">podczas Adres początkowy regionu pamięci, który miał zostać wyliczony.</span><span class="sxs-lookup"><span data-stu-id="db5b8-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="db5b8-107">podczas Rozmiar (w bajtach) obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="db5b8-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db5b8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db5b8-108">Remarks</span></span>  
 <span data-ttu-id="db5b8-109">Metoda `ICLRDataEnumMemoryRegions::EnumMemoryRegions` wywoła tę metodę wywołania zwrotnego po każdej próbie wyliczyć regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="db5b8-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="db5b8-110">Wyliczenie będzie kontynuowane, nawet jeśli ta metoda zwróci błąd wskazujący, że wynik HRESULT.</span><span class="sxs-lookup"><span data-stu-id="db5b8-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="db5b8-111">Regiony zgłaszane przez to wywołanie zwrotne mogą być duplikatami lub nakładanymi regionami.</span><span class="sxs-lookup"><span data-stu-id="db5b8-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db5b8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db5b8-112">Requirements</span></span>  
 <span data-ttu-id="db5b8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db5b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db5b8-114">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="db5b8-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="db5b8-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db5b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db5b8-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db5b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5b8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db5b8-117">See also</span></span>

- [<span data-ttu-id="db5b8-118">ICLRDataEnumMemoryRegionsCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="db5b8-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
