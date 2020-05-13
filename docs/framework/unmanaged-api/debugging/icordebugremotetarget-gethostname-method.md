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
ms.openlocfilehash: 020724c422af7cba0165e6f37d0eacb7742153ec
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379273"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="f3c9b-102">ICorDebugRemoteTarget::GetHostName — Metoda</span><span class="sxs-lookup"><span data-stu-id="f3c9b-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="f3c9b-103">Zwraca w pełni kwalifikowaną nazwę domeny lub adres IPv4 maszyny docelowej zdalnego debugowania.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="f3c9b-104">Protokół IPV6 nie jest w tej chwili obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c9b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3c9b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3c9b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3c9b-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="f3c9b-107">podczas Rozmiar (w znakach) `szHostName` buforu.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="f3c9b-108">Jeśli ten parametr ma wartość 0 (zero), `szHostName` musi mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="f3c9b-109">określoną Liczba znaków, łącznie z terminatorem wartości null, w nazwie hosta lub adresie IP.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="f3c9b-110">Ten parametr może mieć wartość null.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="f3c9b-111">określoną Bufor, który zawiera nazwę hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3c9b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f3c9b-112">Return Value</span></span>  
 <span data-ttu-id="f3c9b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3c9b-113">S_OK</span></span>  
 <span data-ttu-id="f3c9b-114">Nazwa hosta lub adres IP zostały pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="f3c9b-115">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="f3c9b-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f3c9b-116">Nie można zwrócić nazwy hosta lub adresu IP.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3c9b-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3c9b-117">Remarks</span></span>  
 <span data-ttu-id="f3c9b-118">Ta metoda jest implementowana przez składnik zapisywania debugera.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="f3c9b-119">Musi być zgodna z wieloma modelami wywołań: przy pierwszym wywołaniu obiekt wywołujący przekazuje wartość null do obu `cchHostName` i i `szHostName` `pcchHostName` zwraca rozmiar wymaganego buforu.</span><span class="sxs-lookup"><span data-stu-id="f3c9b-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="f3c9b-120">W drugim wywołaniu zostanie przekazana poprzednio zwrócony rozmiar `cchHostName` , a bufor o odpowiednim rozmiarze jest przekazano `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="f3c9b-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3c9b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3c9b-121">Requirements</span></span>  
 <span data-ttu-id="f3c9b-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3c9b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3c9b-123">**Nagłówek:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="f3c9b-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f3c9b-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3c9b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3c9b-125">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="f3c9b-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3c9b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3c9b-126">See also</span></span>

- [<span data-ttu-id="f3c9b-127">ICorDebugRemoteTarget — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f3c9b-127">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="f3c9b-128">ICorDebug — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f3c9b-128">ICorDebug Interface</span></span>](icordebug-interface.md)
