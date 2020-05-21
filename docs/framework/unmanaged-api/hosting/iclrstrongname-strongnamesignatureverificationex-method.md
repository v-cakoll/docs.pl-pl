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
ms.openlocfilehash: e2003ce78f04b101fe093867e0820f9c3840151a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762711"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="5c780-102">ICLRStrongName::StrongNameSignatureVerificationEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c780-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>
<span data-ttu-id="5c780-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5c780-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c780-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c780-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c780-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c780-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5c780-106">podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="5c780-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="5c780-107">[w] `true` Aby przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="5c780-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="5c780-108">[out] `true` Jeśli podpis silnej nazwy został zweryfikowany; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="5c780-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="5c780-109">`pfWasVerified`jest również ustawiony na `false` , Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="5c780-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c780-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5c780-110">Return Value</span></span>  
 <span data-ttu-id="5c780-111">`S_OK`Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="5c780-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c780-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c780-112">Remarks</span></span>  
 <span data-ttu-id="5c780-113">Metoda [ICLRStrongName:: StrongNameSignatureVerificationEx —](iclrstrongname-strongnamesignatureverificationex-method.md) zapewnia możliwość podobną do metody [ICLRStrongName:: StrongNameSignatureVerification —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5c780-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="5c780-114">Jednak drugi parametr wejściowy i parametr wyjściowy dla [ICLRStrongName:: StrongNameSignatureVerificationEx —](iclrstrongname-strongnamesignatureverificationex-method.md) są typu `BOOLEAN` zamiast `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="5c780-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c780-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c780-115">Requirements</span></span>  
 <span data-ttu-id="5c780-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c780-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c780-117">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="5c780-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c780-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5c780-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c780-119">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c780-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c780-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c780-120">See also</span></span>

- [<span data-ttu-id="5c780-121">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="5c780-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="5c780-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c780-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
