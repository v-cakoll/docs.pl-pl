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
ms.openlocfilehash: 0ca7aee79b5b8c3d58b4beb8f1ff886a7d55afab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782710"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="fc0f8-102">ICorDebugRemoteTarget::GetHostName — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc0f8-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="fc0f8-103">Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 zdalnego debugowania komputera docelowego.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="fc0f8-104">Protokół IPv6 nie jest obsługiwany w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0f8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc0f8-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc0f8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc0f8-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="fc0f8-107">[in] Rozmiar, w postaci, z `szHostName` buforu.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="fc0f8-108">Jeśli ten parametr ma wartość 0 (zero), `szHostName` może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="fc0f8-109">[out] Liczba znaków, łącznie z terminatorem null, nazwa hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="fc0f8-110">Ten parametr może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="fc0f8-111">[out] Bufor, który zawiera nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc0f8-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc0f8-112">Return Value</span></span>  
 <span data-ttu-id="fc0f8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc0f8-113">S_OK</span></span>  
 <span data-ttu-id="fc0f8-114">Nazwa hosta lub adres IP została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="fc0f8-115">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="fc0f8-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fc0f8-116">Nie można zwrócić nazwy hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc0f8-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc0f8-117">Remarks</span></span>  
 <span data-ttu-id="fc0f8-118">Ta metoda jest implementowana przez moduł zapisujący debugera.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="fc0f8-119">Musi on być zgodny z paradygmatu wielokrotnego wywołania: Przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null na wartość oba `cchHostName` i `szHostName`, i `pcchHostName` zwraca rozmiar wymaganego buforu.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="fc0f8-120">Przy drugim wywołaniu, rozmiar, który został wcześniej zwrócony jest przekazywany w `cchHostName`, i właściwy rozmiar buforu jest przekazywany w `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="fc0f8-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0f8-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc0f8-121">Requirements</span></span>  
 <span data-ttu-id="fc0f8-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc0f8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0f8-123">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="fc0f8-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="fc0f8-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc0f8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc0f8-125">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="fc0f8-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0f8-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc0f8-126">See also</span></span>

- [<span data-ttu-id="fc0f8-127">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc0f8-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="fc0f8-128">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc0f8-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
