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
ms.openlocfilehash: 3209b42263c62c8296d43ab06b0d89db2dd89be8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665995"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="e31f6-102">StrongNameSignatureVerification — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e31f6-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="e31f6-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy, który jest weryfikowany zgodnie z określone flagi.</span><span class="sxs-lookup"><span data-stu-id="e31f6-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="e31f6-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e31f6-104">This function has been deprecated.</span></span> <span data-ttu-id="e31f6-105">Użyj [iclrstrongname::strongnamesignatureverification —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e31f6-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e31f6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e31f6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e31f6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e31f6-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e31f6-108">[in] Ścieżka do przenośnych (.dll lub .exe) pliku wykonywalnego dla zestawu sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="e31f6-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e31f6-109">[in] Flagi, aby zmodyfikować zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e31f6-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="e31f6-110">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e31f6-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="e31f6-111">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="e31f6-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="e31f6-112">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to manifest jest weryfikowany po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="e31f6-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="e31f6-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="e31f6-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="e31f6-114">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e31f6-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="e31f6-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.</span><span class="sxs-lookup"><span data-stu-id="e31f6-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="e31f6-116">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="e31f6-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e31f6-117">[out] Flagi wskazującą, czy została zweryfikowana podpisu silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e31f6-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="e31f6-118">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="e31f6-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="e31f6-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="e31f6-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e31f6-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e31f6-120">Return Value</span></span>  
 <span data-ttu-id="e31f6-121">`true` Jeśli weryfikacja się powiodła. w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e31f6-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e31f6-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e31f6-122">Requirements</span></span>  
 <span data-ttu-id="e31f6-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e31f6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e31f6-124">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e31f6-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e31f6-125">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e31f6-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e31f6-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e31f6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31f6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e31f6-127">See also</span></span>

- [<span data-ttu-id="e31f6-128">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="e31f6-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="e31f6-129">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="e31f6-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="e31f6-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e31f6-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
