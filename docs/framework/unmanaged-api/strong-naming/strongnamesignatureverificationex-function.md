---
title: "StrongNameSignatureVerificationEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationEx
helpviewer_keywords: StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0aebb53c6718a6812cbe6a6888f389c7b1a52dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="ca0d6-102">StrongNameSignatureVerificationEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ca0d6-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="ca0d6-103">Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="ca0d6-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-104">This function has been deprecated.</span></span> <span data-ttu-id="ca0d6-105">Użyj [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca0d6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca0d6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca0d6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca0d6-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ca0d6-108">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego dla zestawu do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="ca0d6-109">[in] `true` do przeprowadzenia weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="ca0d6-110">[out] `true` Jeśli podpisu silnej nazwy zostało zweryfikowane; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="ca0d6-111">`pfWasVerified`jest również opcja `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca0d6-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ca0d6-112">Return Value</span></span>  
 <span data-ttu-id="ca0d6-113">`true`Jeśli Weryfikacja powiodła się. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca0d6-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca0d6-114">Remarks</span></span>  
 <span data-ttu-id="ca0d6-115">`StrongNameSignatureVerificationEx`zapewnia funkcje podobne do [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="ca0d6-116">Jednak drugą danych wejściowych i parametru wyjściowego dla `StrongNameSignatureVerificationEx` typu `BOOLEAN` zamiast `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ca0d6-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca0d6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca0d6-117">Requirements</span></span>  
 <span data-ttu-id="ca0d6-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca0d6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca0d6-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ca0d6-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ca0d6-120">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ca0d6-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ca0d6-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca0d6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0d6-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca0d6-122">See Also</span></span>  
 [<span data-ttu-id="ca0d6-123">StrongNameSignatureVerificationEx — metoda</span><span class="sxs-lookup"><span data-stu-id="ca0d6-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="ca0d6-124">StrongNameSignatureVerification — metoda</span><span class="sxs-lookup"><span data-stu-id="ca0d6-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="ca0d6-125">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="ca0d6-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
