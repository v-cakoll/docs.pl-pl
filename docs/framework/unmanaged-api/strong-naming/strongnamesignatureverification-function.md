---
title: StrongNameSignatureVerification — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c888c32a0b40d2458a919613e35ca9d1d830c4f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="a1ed0-102">StrongNameSignatureVerification — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a1ed0-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="a1ed0-103">Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy, która zostanie poddana weryfikacji zgodnie z określonym flagi.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="a1ed0-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-104">This function has been deprecated.</span></span> <span data-ttu-id="a1ed0-105">Użyj [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ed0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1ed0-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1ed0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1ed0-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a1ed0-108">[in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu można zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="a1ed0-109">[in] Flagi, aby zmodyfikować zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="a1ed0-110">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a1ed0-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="a1ed0-111">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="a1ed0-112">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to plik manifestu jest weryfikowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="a1ed0-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna będzie zezwalał na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="a1ed0-114">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, czy zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="a1ed0-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, czy pamięć podręczna zapewni żadnych gwarancji ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="a1ed0-116">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="a1ed0-117">[out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="a1ed0-118">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="a1ed0-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="a1ed0-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1ed0-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1ed0-120">Return Value</span></span>  
 <span data-ttu-id="a1ed0-121">`true` Jeśli Weryfikacja powiodła się. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a1ed0-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ed0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1ed0-122">Requirements</span></span>  
 <span data-ttu-id="a1ed0-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ed0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ed0-124">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a1ed0-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a1ed0-125">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1ed0-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1ed0-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ed0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ed0-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1ed0-127">See Also</span></span>  
 [<span data-ttu-id="a1ed0-128">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ed0-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [<span data-ttu-id="a1ed0-129">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="a1ed0-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [<span data-ttu-id="a1ed0-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1ed0-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
