---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860704"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="183ca-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda</span><span class="sxs-lookup"><span data-stu-id="183ca-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="183ca-103">Wylicza określone obszary pamięci.</span><span class="sxs-lookup"><span data-stu-id="183ca-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="183ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="183ca-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="183ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="183ca-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="183ca-106">podczas Wskaźnik do wystąpienia [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) , który jest wywoływany przez tę metodę dla każdego regionu pamięci, który jest wyliczany w celu powiadomienia debugera wyniku.</span><span class="sxs-lookup"><span data-stu-id="183ca-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="183ca-107">Wyliczenie regionów pamięci jest kontynuowane nawet wtedy, gdy wywołanie zwrotne wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="183ca-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="183ca-108">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="183ca-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="183ca-109">podczas Wartość wyliczenia [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) , która określa regiony pamięci do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="183ca-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="183ca-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="183ca-110">Remarks</span></span>  
 <span data-ttu-id="183ca-111">Ta metoda używa określonego wystąpienia [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) do powiadomienia obiektu wywołującego wyniki.</span><span class="sxs-lookup"><span data-stu-id="183ca-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="183ca-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="183ca-112">Requirements</span></span>  
 <span data-ttu-id="183ca-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="183ca-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="183ca-114">**Nagłówek:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="183ca-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="183ca-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="183ca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="183ca-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="183ca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="183ca-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="183ca-117">See also</span></span>

- [<span data-ttu-id="183ca-118">ICLRDataEnumMemoryRegions — Interfejs</span><span class="sxs-lookup"><span data-stu-id="183ca-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
