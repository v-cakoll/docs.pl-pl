---
title: ICLRStrongName::StrongNameSignatureVerification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: d31c9c0db306aad3a7c3472ef6329f25aa6c5902
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762659"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="4dd7f-102">ICLRStrongName::StrongNameSignatureVerification — Metoda</span><span class="sxs-lookup"><span data-stu-id="4dd7f-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="4dd7f-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy, który jest sprawdzany według określonych flag.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dd7f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dd7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dd7f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4dd7f-106">podczas Ścieżka do przenośnego pliku wykonywalnego (. dll lub. exe) dla zestawu do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="4dd7f-107">podczas Flagi modyfikujące zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="4dd7f-108">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="4dd7f-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="4dd7f-109">`SN_INFLAG_FORCE_VER`(0x00000001) — wymusza weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="4dd7f-110">`SN_INFLAG_INSTALL`(0x00000002) — określa, że jest to pierwsze sprawdzenie manifestu.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="4dd7f-111">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) — określa, że pamięć podręczna będzie zezwalać na dostęp tylko użytkownikom z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="4dd7f-112">`SN_INFLAG_USER_ACCESS`(0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="4dd7f-113">`SN_INFLAG_ALL_ACCESS`(0x00000010) — określa, że pamięć podręczna nie będzie zapewniać żadnych gwarancji ograniczenia dostępu.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="4dd7f-114">`SN_INFLAG_RUNTIME`(0x80000000) — zarezerwowane do debugowania wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="4dd7f-115">określoną Flagi wskazujące, czy podpis silnej nazwy został zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="4dd7f-116">Obsługiwana jest następująca wartość:</span><span class="sxs-lookup"><span data-stu-id="4dd7f-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="4dd7f-117">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) — ta wartość jest ustawiona na `false` , aby określić, że weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="4dd7f-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dd7f-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4dd7f-118">Return Value</span></span>  
 <span data-ttu-id="4dd7f-119">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="4dd7f-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd7f-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dd7f-120">Requirements</span></span>  
 <span data-ttu-id="4dd7f-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd7f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd7f-122">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="4dd7f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4dd7f-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4dd7f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dd7f-124">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd7f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd7f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4dd7f-125">See also</span></span>

- [<span data-ttu-id="4dd7f-126">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="4dd7f-126">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="4dd7f-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dd7f-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
