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
ms.openlocfilehash: e4fa0a3745200d39a468292e9520b1aeb0e9f1b2
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860671"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a><span data-ttu-id="3dc58-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda</span><span class="sxs-lookup"><span data-stu-id="3dc58-102">ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion Method</span></span>
<span data-ttu-id="3dc58-103">Wywoływane przez [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera, wynik próby wyliczenia określonego regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dc58-103">Called by [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) to report to the debugger the result of an attempt to enumerate a specified region of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dc58-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dc58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dc58-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3dc58-106">podczas Adres początkowy regionu pamięci, który miał zostać wyliczony.</span><span class="sxs-lookup"><span data-stu-id="3dc58-106">[in] The starting address of the memory region that was to be enumerated.</span></span>  
  
 `size`  
 <span data-ttu-id="3dc58-107">podczas Rozmiar (w bajtach) obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dc58-107">[in] The size, in bytes, of the memory region.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc58-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dc58-108">Remarks</span></span>  
 <span data-ttu-id="3dc58-109">`ICLRDataEnumMemoryRegions::EnumMemoryRegions` Metoda wywoła tę metodę wywołania zwrotnego po każdej próbie wyliczenia regionu pamięci.</span><span class="sxs-lookup"><span data-stu-id="3dc58-109">The `ICLRDataEnumMemoryRegions::EnumMemoryRegions` method will call this callback method after each attempt to enumerate a memory region.</span></span> <span data-ttu-id="3dc58-110">Wyliczenie będzie kontynuowane, nawet jeśli ta metoda zwróci błąd wskazujący, że wynik HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3dc58-110">The enumeration will continue even if this method returns an HRESULT indicating failure.</span></span>  
  
 <span data-ttu-id="3dc58-111">Regiony zgłaszane przez to wywołanie zwrotne mogą być duplikatami lub nakładanymi regionami.</span><span class="sxs-lookup"><span data-stu-id="3dc58-111">Regions reported by this callback may be duplicates or overlapping regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dc58-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3dc58-112">Requirements</span></span>  
 <span data-ttu-id="3dc58-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dc58-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dc58-114">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="3dc58-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3dc58-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3dc58-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dc58-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dc58-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dc58-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dc58-117">See also</span></span>

- [<span data-ttu-id="3dc58-118">ICLRDataEnumMemoryRegionsCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3dc58-118">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](iclrdataenummemoryregionscallback-interface.md)
