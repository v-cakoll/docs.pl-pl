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
ms.openlocfilehash: df2eb9d454f2037ef5f2a09d1309d52a8365e715
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782686"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="073cf-102">StrongNameSignatureVerificationFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="073cf-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="073cf-103">Sprawdza, czy zestaw, który został już zmapowany do pamięci jest prawidłowa dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="073cf-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="073cf-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="073cf-104">This function has been deprecated.</span></span> <span data-ttu-id="073cf-105">Użyj [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="073cf-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="073cf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="073cf-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="073cf-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="073cf-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="073cf-108">[in] Względna wirtualny adres manifestu zestawu zamapowany.</span><span class="sxs-lookup"><span data-stu-id="073cf-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="073cf-109">[in] Rozmiar w bajtach zamapowanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="073cf-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="073cf-110">[in] Flagi, które wpływają na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="073cf-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="073cf-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="073cf-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="073cf-112">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="073cf-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="073cf-113">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest pierwszej weryfikacji wykonywane w tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="073cf-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="073cf-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="073cf-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="073cf-115">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="073cf-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="073cf-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.</span><span class="sxs-lookup"><span data-stu-id="073cf-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="073cf-117">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="073cf-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="073cf-118">[out] Flaga informacji dodatkowych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="073cf-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="073cf-119">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="073cf-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="073cf-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="073cf-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="073cf-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="073cf-121">Return Value</span></span>  
 <span data-ttu-id="073cf-122">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="073cf-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="073cf-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="073cf-123">Remarks</span></span>  
 <span data-ttu-id="073cf-124">Jeśli `StrongNameSignatureVerificationFromImage` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="073cf-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="073cf-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="073cf-125">Requirements</span></span>  
 <span data-ttu-id="073cf-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="073cf-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="073cf-127">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="073cf-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="073cf-128">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="073cf-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="073cf-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="073cf-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073cf-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="073cf-130">See also</span></span>

- [<span data-ttu-id="073cf-131">StrongNameSignatureVerificationFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="073cf-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="073cf-132">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="073cf-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
