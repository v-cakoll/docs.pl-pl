---
title: StrongNameSignatureVerificationEx2 — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8b3096bd0c60e826fec4c8daf535c3c4086630
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482785"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="883ef-102">StrongNameSignatureVerificationEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="883ef-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="883ef-103">Weryfikuje podpis zestaw o silnej nazwie, a następnie udostępnia mapowanie klucz ECMA do rzeczywistego klucza.</span><span class="sxs-lookup"><span data-stu-id="883ef-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="883ef-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="883ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="883ef-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="883ef-106">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego w zestawie, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="883ef-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="883ef-107">[in] `true` przeprowadzić weryfikację, nawet jeśli jest to konieczne zastąpić ustawienia rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="883ef-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="883ef-108">[in] Wskaźnik do mapowania z ECMA klucza publicznego do rzeczywistego klucza używany podczas weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="883ef-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="883ef-109">[in] Długość klucza publicznego rzeczywistych ECMA.</span><span class="sxs-lookup"><span data-stu-id="883ef-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="883ef-110">[out] `true` Jeśli podpisu silnej nazwy został zweryfikowany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="883ef-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="883ef-111">Ten parametr jest również ustawiona na `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="883ef-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="883ef-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="883ef-112">Return Value</span></span>  
 <span data-ttu-id="883ef-113">`S_OK` Jeśli weryfikacja się powiodła. w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="883ef-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883ef-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="883ef-114">Requirements</span></span>  
 <span data-ttu-id="883ef-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="883ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883ef-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="883ef-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="883ef-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="883ef-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="883ef-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883ef-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="883ef-119">See also</span></span>
- [<span data-ttu-id="883ef-120">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="883ef-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="883ef-121">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="883ef-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="883ef-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="883ef-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
