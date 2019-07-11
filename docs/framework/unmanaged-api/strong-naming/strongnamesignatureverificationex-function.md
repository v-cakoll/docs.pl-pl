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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80df33e9064d9843873c67272bac7a34dbe734cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751613"
---
# <a name="strongnamesignatureverificationex-function"></a><span data-ttu-id="cbf4e-102">StrongNameSignatureVerificationEx — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cbf4e-102">StrongNameSignatureVerificationEx Function</span></span>
<span data-ttu-id="cbf4e-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
 <span data-ttu-id="cbf4e-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-104">This function has been deprecated.</span></span> <span data-ttu-id="cbf4e-105">Użyj [iclrstrongname::strongnamesignatureverificationex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-105">Use the [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf4e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbf4e-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbf4e-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbf4e-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="cbf4e-108">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego w zestawie, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-108">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="cbf4e-109">[in] `true` przeprowadzić weryfikację, nawet jeśli jest to konieczne zastąpić ustawienia rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-109">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="cbf4e-110">[out] `true` Jeśli podpisu silnej nazwy został zweryfikowany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="cbf4e-111">`pfWasVerified` jest również ustawiona na `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-111">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbf4e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cbf4e-112">Return Value</span></span>  
 <span data-ttu-id="cbf4e-113">`true` Jeśli weryfikacja się powiodła. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-113">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbf4e-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbf4e-114">Remarks</span></span>  
 <span data-ttu-id="cbf4e-115">`StrongNameSignatureVerificationEx` zapewnia możliwości podobne do [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-115">`StrongNameSignatureVerificationEx` provides a capability similar to the [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md) function.</span></span> <span data-ttu-id="cbf4e-116">Jednak drugi dane wejściowe i parametru wyjściowego dla `StrongNameSignatureVerificationEx` typu `BOOLEAN` zamiast `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="cbf4e-116">However, the second input parameter and the output parameter for `StrongNameSignatureVerificationEx` are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbf4e-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbf4e-117">Requirements</span></span>  
 <span data-ttu-id="cbf4e-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbf4e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbf4e-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cbf4e-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cbf4e-120">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cbf4e-120">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="cbf4e-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbf4e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf4e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbf4e-122">See also</span></span>

- [<span data-ttu-id="cbf4e-123">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="cbf4e-123">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="cbf4e-124">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="cbf4e-124">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="cbf4e-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="cbf4e-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
