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
ms.openlocfilehash: ad25603f5acd32aa21192f86364976eb93d23540
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717548"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="3c17f-102">ICLRStrongName::StrongNameSignatureVerificationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c17f-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="3c17f-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3c17f-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c17f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c17f-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c17f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c17f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3c17f-106">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego w zestawie, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="3c17f-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="3c17f-107">[in] `true` przeprowadzić weryfikację, nawet jeśli jest to konieczne zastąpić ustawienia rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3c17f-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="3c17f-108">[out] `true` Jeśli podpisu silnej nazwy został zweryfikowany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3c17f-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="3c17f-109">`pfWasVerified` jest również ustawiona na `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="3c17f-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c17f-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c17f-110">Return Value</span></span>  
 <span data-ttu-id="3c17f-111">`S_OK` Jeśli weryfikacja się powiodła. w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="3c17f-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c17f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c17f-112">Remarks</span></span>  
 <span data-ttu-id="3c17f-113">[Iclrstrongname::strongnamesignatureverificationex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) metoda zapewnia możliwości podobne do [iclrstrongname::strongnamesignatureverification —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3c17f-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="3c17f-114">Jednak drugi dane wejściowe i parametru wyjściowego dla [iclrstrongname::strongnamesignatureverificationex —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) typu `BOOLEAN` zamiast `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="3c17f-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c17f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c17f-115">Requirements</span></span>  
 <span data-ttu-id="3c17f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c17f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c17f-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3c17f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3c17f-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c17f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c17f-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c17f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c17f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c17f-120">See also</span></span>
- [<span data-ttu-id="3c17f-121">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="3c17f-121">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="3c17f-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c17f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
