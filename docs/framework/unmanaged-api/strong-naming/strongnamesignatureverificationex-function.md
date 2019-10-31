---
title: StrongNameSignatureVerificationEx — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
ms.openlocfilehash: ca428d680df1710d8e74441d9945d4c3545b0482
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121148"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="d5a95-102">StrongNameSignatureVerificationEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d5a95-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="d5a95-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d5a95-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="d5a95-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d5a95-104">This function has been deprecated.</span></span> <span data-ttu-id="d5a95-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureVerificationEx —](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d5a95-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a95-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5a95-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5a95-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5a95-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d5a95-108">podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="d5a95-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="d5a95-109">[in] `true` przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d5a95-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="d5a95-110">[out] `true`, jeśli zweryfikowano podpis silnej nazwy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d5a95-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="d5a95-111">`pfWasVerified` jest również ustawiony na `false`, Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="d5a95-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5a95-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d5a95-112">Return Value</span></span>  
 <span data-ttu-id="d5a95-113">`true`, Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d5a95-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a95-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5a95-114">Remarks</span></span>  
 <span data-ttu-id="d5a95-115">`StrongNameSignatureVerificationEx` zapewnia możliwość podobną do funkcji [StrongNameSignatureVerification —](strongnamesignatureverification-function.md) .</span><span class="sxs-lookup"><span data-stu-id="d5a95-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="d5a95-116">Jednak drugi parametr wejściowy i parametr wyjściowy dla `StrongNameSignatureVerificationEx` są typu `BOOLEAN` zamiast `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="d5a95-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5a95-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5a95-117">Requirements</span></span>  
 <span data-ttu-id="d5a95-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5a95-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5a95-119">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="d5a95-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d5a95-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d5a95-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="d5a95-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5a95-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a95-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5a95-122">See also</span></span>

- [<span data-ttu-id="d5a95-123">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="d5a95-123">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="d5a95-124">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="d5a95-124">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="d5a95-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5a95-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
