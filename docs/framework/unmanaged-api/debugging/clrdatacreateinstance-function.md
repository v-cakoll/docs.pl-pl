---
title: CLRDataCreateInstance — Funkcja
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
ms.openlocfilehash: 71836108dbd0ce01a64b4d9ac773c28d385dfd7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099689"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="5f509-102">CLRDataCreateInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="5f509-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="5f509-103">Tworzy obiekt interfejsu dla określonego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5f509-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f509-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f509-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f509-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f509-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="5f509-106">podczas Identyfikator interfejsu, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="5f509-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="5f509-107">podczas Wskaźnik do obiektu [ICLRDataTarget](iclrdatatarget-interface.md) zaimplementowanego przez użytkownika, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5f509-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="5f509-108">określoną Wskaźnik do adresu zwróconego obiektu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5f509-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f509-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f509-109">Remarks</span></span>  
 <span data-ttu-id="5f509-110">Obiekt `ICLRDataTarget` jest implementowany przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="5f509-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="5f509-111">Implementacja zależy od typu reprezentowanego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="5f509-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="5f509-112">Element docelowy może być procesem, zrzutem pamięci, maszyną zdalną i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5f509-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f509-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f509-113">Requirements</span></span>  
 <span data-ttu-id="5f509-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f509-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f509-115">**Nagłówek:** ClrData. idl</span><span class="sxs-lookup"><span data-stu-id="5f509-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="5f509-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5f509-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f509-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f509-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f509-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f509-118">See also</span></span>

- [<span data-ttu-id="5f509-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="5f509-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
