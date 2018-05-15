---
title: ICLRStrongName::StrongNameSignatureVerificationEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 933b8385a336a087f7af5245024af209582120cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="50f14-102">ICLRStrongName::StrongNameSignatureVerificationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="50f14-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="50f14-103">Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="50f14-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f14-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50f14-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50f14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50f14-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="50f14-106">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego dla zestawu do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="50f14-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="50f14-107">[in] `true` do przeprowadzenia weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="50f14-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="50f14-108">[out] `true` Jeśli podpisu silnej nazwy zostało zweryfikowane; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="50f14-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="50f14-109">`pfWasVerified` jest również opcja `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="50f14-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f14-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50f14-110">Return Value</span></span>  
 <span data-ttu-id="50f14-111">`S_OK` Jeśli Weryfikacja powiodła się. w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="50f14-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50f14-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50f14-112">Remarks</span></span>  
 <span data-ttu-id="50f14-113">[ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metody udostępnia funkcję podobny do [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="50f14-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="50f14-114">Jednak drugą danych wejściowych i parametru wyjściowego dla [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) typu `BOOLEAN` zamiast `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="50f14-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f14-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50f14-115">Requirements</span></span>  
 <span data-ttu-id="50f14-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50f14-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f14-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="50f14-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50f14-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50f14-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50f14-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50f14-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f14-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50f14-120">See Also</span></span>  
 [<span data-ttu-id="50f14-121">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="50f14-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="50f14-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="50f14-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
