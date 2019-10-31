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
ms.openlocfilehash: a9a6ca9ae3cdb1c6a7398d08c9f99e3cde125cf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131897"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="463b2-102">ICorDebugRemoteTarget::GetHostName — Metoda</span><span class="sxs-lookup"><span data-stu-id="463b2-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="463b2-103">Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 maszyny docelowej zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="463b2-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="463b2-104">Protokół IPV6 nie jest w tej chwili obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="463b2-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="463b2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="463b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="463b2-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="463b2-107">podczas Rozmiar, w znakach, buforu `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="463b2-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="463b2-108">Jeśli ten parametr ma wartość 0 (zero), `szHostName` musi mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="463b2-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="463b2-109">określoną Liczba znaków, łącznie z terminatorem wartości null, w nazwie hosta lub adresie IP.</span><span class="sxs-lookup"><span data-stu-id="463b2-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="463b2-110">Ten parametr może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="463b2-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="463b2-111">określoną Bufor, który zawiera nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="463b2-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="463b2-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="463b2-112">Return Value</span></span>  
 <span data-ttu-id="463b2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="463b2-113">S_OK</span></span>  
 <span data-ttu-id="463b2-114">Nazwa hosta lub adres IP zostały pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="463b2-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="463b2-115">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="463b2-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="463b2-116">Nie można zwrócić nazwy hosta lub adresu IP.</span><span class="sxs-lookup"><span data-stu-id="463b2-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="463b2-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="463b2-117">Remarks</span></span>  
 <span data-ttu-id="463b2-118">Ta metoda jest implementowana przez składnik zapisywania debugera.</span><span class="sxs-lookup"><span data-stu-id="463b2-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="463b2-119">Musi być zgodna z wieloma modelami wywołań: przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null do obu `cchHostName` i `szHostName`, a `pcchHostName` zwraca rozmiar wymaganego buforu.</span><span class="sxs-lookup"><span data-stu-id="463b2-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="463b2-120">W drugim wywołaniu rozmiar, który został wcześniej zwrócony, jest przesyłany w `cchHostName`, a bufor o odpowiednim rozmiarze jest przekazana w `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="463b2-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="463b2-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="463b2-121">Requirements</span></span>  
 <span data-ttu-id="463b2-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="463b2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="463b2-123">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="463b2-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="463b2-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="463b2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="463b2-125">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="463b2-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463b2-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="463b2-126">See also</span></span>

- [<span data-ttu-id="463b2-127">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="463b2-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="463b2-128">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="463b2-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
