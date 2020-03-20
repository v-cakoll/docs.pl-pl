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
ms.openlocfilehash: c24963a6e56adfb9f763c6521027744db82cc357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179360"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="191c0-102">CLRDataCreateInstance — Funkcja</span><span class="sxs-lookup"><span data-stu-id="191c0-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="191c0-103">Tworzy obiekt interfejsu dla określonego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="191c0-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="191c0-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,
    [in]  ICLRDataTarget  *target,
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="191c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="191c0-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="191c0-106">[w] Identyfikator interfejsu, który ma zostać skreślony.</span><span class="sxs-lookup"><span data-stu-id="191c0-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="191c0-107">[w] Wskaźnik do obiektu [ICLRDataTarget](iclrdatatarget-interface.md) zaimplementowanego przez użytkownika, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="191c0-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="191c0-108">[na zewnątrz] Wskaźnik do adresu zwracanego obiektu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="191c0-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="191c0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="191c0-109">Remarks</span></span>  
 <span data-ttu-id="191c0-110">Obiekt `ICLRDataTarget` jest implementowany przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="191c0-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="191c0-111">Implementacja zależy od typu elementu docelowego reprezentowanego.</span><span class="sxs-lookup"><span data-stu-id="191c0-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="191c0-112">Element docelowy może być procesem, zrzutem pamięci, komputerem zdalnym i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="191c0-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="191c0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="191c0-113">Requirements</span></span>  
 <span data-ttu-id="191c0-114">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="191c0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="191c0-115">**Nagłówek:** Plik ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="191c0-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="191c0-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="191c0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="191c0-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="191c0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="191c0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="191c0-118">See also</span></span>

- [<span data-ttu-id="191c0-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="191c0-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
