---
title: ICorDebugRemoteTarget::GetHostName — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1536a89d0e85480d3829939c40cd986fe65883df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422474"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="fa120-102">ICorDebugRemoteTarget::GetHostName — Metoda</span><span class="sxs-lookup"><span data-stu-id="fa120-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="fa120-103">Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 zdalnego debugowania maszyny docelowej.</span><span class="sxs-lookup"><span data-stu-id="fa120-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="fa120-104">Protokół IPv6 nie jest obsługiwany w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="fa120-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa120-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa120-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa120-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa120-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="fa120-107">[in] Rozmiar w znaków z `szHostName` buforu.</span><span class="sxs-lookup"><span data-stu-id="fa120-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="fa120-108">Jeśli ten parametr ma wartość 0 (zero), `szHostName` może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="fa120-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="fa120-109">[out] Liczba znaków, włącznie z terminatorem null, nazwa hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fa120-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="fa120-110">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="fa120-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="fa120-111">[out] Bufor, który zawiera nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fa120-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa120-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fa120-112">Return Value</span></span>  
 <span data-ttu-id="fa120-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa120-113">S_OK</span></span>  
 <span data-ttu-id="fa120-114">Pomyślnie zwrócono nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fa120-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="fa120-115">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="fa120-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fa120-116">Nie można zwrócić nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fa120-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa120-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa120-117">Remarks</span></span>  
 <span data-ttu-id="fa120-118">Ta metoda jest implementowany przez twórcę debugera.</span><span class="sxs-lookup"><span data-stu-id="fa120-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="fa120-119">Należy wykonać wiele modelu wywołania: przy pierwszym wywołaniu wywołujący wartości null zarówno `cchHostName` i `szHostName`, i `pcchHostName` zwraca rozmiar buforu wymagane.</span><span class="sxs-lookup"><span data-stu-id="fa120-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="fa120-120">Na drugie wywołanie, rozmiar, który został wcześniej zostały zwrócone jest przekazywany w `cchHostName`, i odpowiednio rozmiar buforu jest przekazywany w `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="fa120-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa120-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa120-121">Requirements</span></span>  
 <span data-ttu-id="fa120-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa120-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa120-123">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="fa120-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fa120-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa120-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa120-125">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="fa120-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa120-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa120-126">See Also</span></span>  
 [<span data-ttu-id="fa120-127">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa120-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="fa120-128">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa120-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
