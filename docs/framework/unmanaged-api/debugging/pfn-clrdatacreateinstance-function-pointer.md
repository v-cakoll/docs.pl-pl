---
title: PFN_CLRDataCreateInstance — Wskaźnik funkcji
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 34aae3cd913465bc3167d6c5eee9873d212fa4ac
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420695"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="ff90a-102">PFN_CLRDataCreateInstance — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="ff90a-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="ff90a-103">Wskazuje funkcję, która tworzy obiekt interfejsu dla określonego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ff90a-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff90a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff90a-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff90a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff90a-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="ff90a-106">podczas Identyfikator interfejsu, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="ff90a-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="ff90a-107">podczas Wskaźnik do obiektu [ICLRDataTarget](iclrdatatarget-interface.md) zaimplementowanego przez użytkownika, który reprezentuje element docelowy, dla którego ma zostać utworzony obiekt interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ff90a-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="ff90a-108">określoną Wskaźnik do adresu zwróconego obiektu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ff90a-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff90a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff90a-109">Remarks</span></span>  
 <span data-ttu-id="ff90a-110">`ICLRDataTarget`Obiekt jest implementowany przez moduł zapisujący aplikacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="ff90a-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="ff90a-111">Implementacja zależy od typu reprezentowanego elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ff90a-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="ff90a-112">Element docelowy może być procesem, zrzutem pamięci, maszyną zdalną i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ff90a-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff90a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff90a-113">Requirements</span></span>  
 <span data-ttu-id="ff90a-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff90a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff90a-115">**Nagłówek:** ClrData. idl</span><span class="sxs-lookup"><span data-stu-id="ff90a-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="ff90a-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff90a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff90a-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff90a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff90a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff90a-118">See also</span></span>

- [<span data-ttu-id="ff90a-119">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="ff90a-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
