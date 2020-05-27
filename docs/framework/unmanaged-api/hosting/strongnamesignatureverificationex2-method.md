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
ms.openlocfilehash: 5e6f77b9b5da061a75d23d7f3f7b673754b62afd
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006370"
---
# <a name="strongnamesignatureverificationex2-method"></a><span data-ttu-id="3b3db-102">StrongNameSignatureVerificationEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b3db-102">StrongNameSignatureVerificationEx2 Method</span></span>
<span data-ttu-id="3b3db-103">Weryfikuje podpis zestawu o silnej nazwie i zapewnia mapowanie z klucza ECMA do klucza rzeczywistego.</span><span class="sxs-lookup"><span data-stu-id="3b3db-103">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b3db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b3db-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b3db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b3db-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3b3db-106">podczas Ścieżka do przenośnego pliku wykonywalnego (. exe lub. dll) dla zestawu, który ma zostać zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="3b3db-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="3b3db-107">[w] `true` Aby przeprowadzić weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="3b3db-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pbEcmaPublicKey`  
 <span data-ttu-id="3b3db-108">podczas Wskaźnik do mapowania z klucza publicznego ECMA do rzeczywistego klucza używanego do weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="3b3db-108">[in] A pointer to the mapping from the ECMA public key to the real key used for verification.</span></span>  
  
 `cbEcmaPublicKey`  
 <span data-ttu-id="3b3db-109">podczas Długość rzeczywistego klucza publicznego ECMA.</span><span class="sxs-lookup"><span data-stu-id="3b3db-109">[in] The length of the real ECMA public key.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="3b3db-110">[out] `true` Jeśli podpis silnej nazwy został zweryfikowany; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="3b3db-110">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="3b3db-111">Ten parametr jest również ustawiony na, `false` Jeśli weryfikacja zakończyła się pomyślnie z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="3b3db-111">This parameter is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b3db-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b3db-112">Return Value</span></span>  
 <span data-ttu-id="3b3db-113">`S_OK`Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="3b3db-113">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b3db-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b3db-114">Requirements</span></span>  
 <span data-ttu-id="3b3db-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b3db-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b3db-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="3b3db-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3b3db-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b3db-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b3db-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b3db-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b3db-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b3db-119">See also</span></span>

- [<span data-ttu-id="3b3db-120">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="3b3db-120">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="3b3db-121">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="3b3db-121">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="3b3db-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b3db-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
