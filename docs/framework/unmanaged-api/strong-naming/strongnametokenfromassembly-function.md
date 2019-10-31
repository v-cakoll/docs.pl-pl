---
title: StrongNameTokenFromAssembly — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
ms.openlocfilehash: 6b9eca3f2f0267870866874ea27dc65812795f41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121131"
---
# <a name="strongnametokenfromassembly-function"></a><span data-ttu-id="9941f-102">StrongNameTokenFromAssembly — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9941f-102">StrongNameTokenFromAssembly Function</span></span>
<span data-ttu-id="9941f-103">Tworzy token silnej nazwy z określonego pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="9941f-103">Creates a strong name token from the specified assembly file.</span></span>  
  
 <span data-ttu-id="9941f-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9941f-104">This function has been deprecated.</span></span> <span data-ttu-id="9941f-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromAssembly —](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9941f-105">Use the [ICLRStrongName::StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9941f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9941f-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9941f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9941f-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="9941f-108">podczas Ścieżka do przenośnego pliku wykonywalnego (PE) dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="9941f-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="9941f-109">określoną Zwrócony token silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9941f-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="9941f-110">określoną Rozmiar (w bajtach) tokenu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="9941f-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9941f-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9941f-111">Return Value</span></span>  
 <span data-ttu-id="9941f-112">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9941f-112">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9941f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9941f-113">Remarks</span></span>  
 <span data-ttu-id="9941f-114">Token silnej nazwy to skrócona postać klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="9941f-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="9941f-115">Token jest 64-bitowym skrótem, który jest tworzony na podstawie klucza publicznego używanego do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="9941f-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="9941f-116">Token jest częścią silnej nazwy zestawu i można go odczytać z metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="9941f-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="9941f-117">Po utworzeniu tokenu należy wywołać funkcję [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) , aby zwolnić przydzieloną pamięć.</span><span class="sxs-lookup"><span data-stu-id="9941f-117">After the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="9941f-118">Jeśli funkcja `StrongNameTokenFromAssembly` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="9941f-118">If the `StrongNameTokenFromAssembly` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9941f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9941f-119">Requirements</span></span>  
 <span data-ttu-id="9941f-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9941f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9941f-121">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9941f-121">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9941f-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9941f-122">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9941f-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9941f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9941f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9941f-124">See also</span></span>

- [<span data-ttu-id="9941f-125">StrongNameTokenFromAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="9941f-125">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="9941f-126">StrongNameTokenFromAssemblyEx, metoda</span><span class="sxs-lookup"><span data-stu-id="9941f-126">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="9941f-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="9941f-127">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
