---
title: StrongNameSignatureVerificationFromImage — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 919c746b738246d76e90730c42882bfdd3ac6edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458724"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="9d666-102">StrongNameSignatureVerificationFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="9d666-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="9d666-103">Sprawdza, czy zestaw, który został już zmapowany do pamięci jest nieprawidłowa dla klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="9d666-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="9d666-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9d666-104">This function has been deprecated.</span></span> <span data-ttu-id="9d666-105">Użyj [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="9d666-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d666-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d666-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d666-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d666-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="9d666-108">[in] Wirtualny adres względny manifestu zestawu mapowane.</span><span class="sxs-lookup"><span data-stu-id="9d666-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9d666-109">[in] Rozmiar w bajtach zamapowanych obrazu.</span><span class="sxs-lookup"><span data-stu-id="9d666-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="9d666-110">[in] Flagi wpływające na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="9d666-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="9d666-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="9d666-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="9d666-112">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikacji, nawet jeśli jest konieczne w celu zastąpienia ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="9d666-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="9d666-113">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to pierwszy weryfikacji wykonywane na ten obraz.</span><span class="sxs-lookup"><span data-stu-id="9d666-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="9d666-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna będzie zezwalał na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="9d666-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="9d666-115">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, czy zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9d666-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="9d666-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, czy pamięć podręczna zapewni żadnych gwarancji ograniczeń dostępu.</span><span class="sxs-lookup"><span data-stu-id="9d666-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="9d666-117">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="9d666-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="9d666-118">[out] Flaga informacje dodatkowe dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9d666-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="9d666-119">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="9d666-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="9d666-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="9d666-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d666-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9d666-121">Return Value</span></span>  
 <span data-ttu-id="9d666-122">`true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="9d666-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d666-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d666-123">Remarks</span></span>  
 <span data-ttu-id="9d666-124">Jeśli `StrongNameSignatureVerificationFromImage` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="9d666-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d666-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d666-125">Requirements</span></span>  
 <span data-ttu-id="9d666-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d666-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d666-127">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9d666-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9d666-128">**Biblioteka:** uwzględnione jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9d666-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="9d666-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d666-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d666-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d666-130">See Also</span></span>  
 [<span data-ttu-id="9d666-131">StrongNameSignatureVerificationFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="9d666-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [<span data-ttu-id="9d666-132">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d666-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
