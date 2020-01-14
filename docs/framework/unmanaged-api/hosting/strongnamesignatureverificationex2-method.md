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
ms.openlocfilehash: 81640e8e34335898f4dd7f4f43eafbd3ef191d19
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938153"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="606be-102">StrongNameSignatureVerificationEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="606be-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="606be-103">Weryfikuje podpis zestawu o silnej nazwie i zapewnia mapowanie z klucza ECMA do klucza rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="606be-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="606be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="606be-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="606be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="606be-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="606be-106">podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="606be-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="606be-107">[in] `true` przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="606be-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="606be-108">podczas Wskaźnik do mapowania z klucza publicznego ECMA do rzeczywistego klucza używanego do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="606be-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="606be-109">podczas Długość rzeczywistego klucza publicznego ECMA.</span><span class="sxs-lookup"><span data-stu-id="606be-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="606be-110">[out] `true`, jeśli zweryfikowano podpis silnej nazwy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="606be-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="606be-111">Ten parametr jest również ustawiany na `false`, Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="606be-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="606be-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="606be-112">Return Value</span></span>  
 <span data-ttu-id="606be-113">`S_OK`, Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="606be-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="606be-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="606be-114">Requirements</span></span>  
 <span data-ttu-id="606be-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="606be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="606be-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="606be-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="606be-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="606be-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="606be-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="606be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="606be-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="606be-119">See also</span></span>

- [<span data-ttu-id="606be-120">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="606be-120">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="606be-121">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="606be-121">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="606be-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="606be-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
