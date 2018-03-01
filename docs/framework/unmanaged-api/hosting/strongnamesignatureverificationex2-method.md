---
title: "StrongNameSignatureVerificationEx2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b4faa7fee32d9cab5a75772f29d2014473e2bee0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="18319-102">StrongNameSignatureVerificationEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="18319-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="18319-103">Weryfikuje podpis zestawu o silnej nazwie i udostępnia mapowanie z ECMA klucza do rzeczywistego klucza.</span><span class="sxs-lookup"><span data-stu-id="18319-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18319-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18319-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18319-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18319-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="18319-106">[in] Ścieżka do przenośnych (.exe lub .dll) pliku wykonywalnego dla zestawu do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="18319-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="18319-107">[in] `true` do przeprowadzenia weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="18319-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="18319-108">[in] Wskaźnik do mapowania z ECMA klucza publicznego do rzeczywistego klucza używany podczas weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="18319-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="18319-109">[in] Długość rzeczywista ECMA klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="18319-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="18319-110">[out] `true` Jeśli podpisu silnej nazwy zostało zweryfikowane; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="18319-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="18319-111">Ten parametr jest również wartość `false` Jeśli Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="18319-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18319-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="18319-112">Return Value</span></span>  
 <span data-ttu-id="18319-113">`S_OK`Jeśli Weryfikacja powiodła się. w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="18319-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18319-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18319-114">Requirements</span></span>  
 <span data-ttu-id="18319-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18319-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18319-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="18319-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="18319-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18319-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18319-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18319-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18319-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18319-119">See Also</span></span>  
 [<span data-ttu-id="18319-120">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="18319-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="18319-121">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="18319-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="18319-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="18319-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
