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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49041031742332fbc275a9dbde91e640eb428c28
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276698"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="83bd6-102">ICLRStrongName::StrongNameSignatureVerification — Metoda</span><span class="sxs-lookup"><span data-stu-id="83bd6-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="83bd6-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy, który jest weryfikowany zgodnie z określone flagi.</span><span class="sxs-lookup"><span data-stu-id="83bd6-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83bd6-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83bd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83bd6-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="83bd6-106">[in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="83bd6-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="83bd6-107">[in] Flagi, aby zmodyfikować zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="83bd6-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="83bd6-108">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="83bd6-108">The following values are supported:</span></span>  
  
-   <span data-ttu-id="83bd6-109">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="83bd6-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="83bd6-110">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to manifest jest weryfikowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="83bd6-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="83bd6-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="83bd6-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="83bd6-112">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="83bd6-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="83bd6-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.</span><span class="sxs-lookup"><span data-stu-id="83bd6-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="83bd6-114">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="83bd6-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="83bd6-115">[out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="83bd6-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="83bd6-116">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="83bd6-116">The following value is supported:</span></span>  
  
-   <span data-ttu-id="83bd6-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="83bd6-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83bd6-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83bd6-118">Return Value</span></span>  
 <span data-ttu-id="83bd6-119">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="83bd6-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83bd6-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83bd6-120">Requirements</span></span>  
 <span data-ttu-id="83bd6-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83bd6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bd6-122">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="83bd6-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="83bd6-123">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83bd6-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83bd6-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83bd6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bd6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83bd6-125">See Also</span></span>  
 [<span data-ttu-id="83bd6-126">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="83bd6-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="83bd6-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="83bd6-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
