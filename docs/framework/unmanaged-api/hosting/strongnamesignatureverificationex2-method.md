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
ms.openlocfilehash: cf8d6b7e45c0012d223173c85a92fac4fb044c6c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141414"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="fe9ce-102">StrongNameSignatureVerificationEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe9ce-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="fe9ce-103">Weryfikuje podpis zestawu o silnej nazwie i zapewnia mapowanie z klucza ECMA do klucza rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe9ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe9ce-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe9ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe9ce-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fe9ce-106">podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="fe9ce-107">[in] `true` przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="fe9ce-108">podczas Wskaźnik do mapowania z klucza publicznego ECMA do rzeczywistego klucza używanego do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="fe9ce-109">podczas Długość rzeczywistego klucza publicznego ECMA.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="fe9ce-110">[out] `true`, jeśli zweryfikowano podpis silnej nazwy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="fe9ce-111">Ten parametr jest również ustawiany na `false`, Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="fe9ce-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe9ce-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe9ce-112">Return Value</span></span>  
 <span data-ttu-id="fe9ce-113">`S_OK`, Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="fe9ce-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe9ce-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe9ce-114">Requirements</span></span>  
 <span data-ttu-id="fe9ce-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe9ce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe9ce-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="fe9ce-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fe9ce-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe9ce-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe9ce-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9ce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9ce-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe9ce-119">See also</span></span>

- [<span data-ttu-id="fe9ce-120">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="fe9ce-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="fe9ce-121">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="fe9ce-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="fe9ce-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe9ce-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
