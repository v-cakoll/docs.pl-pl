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
ms.openlocfilehash: 54b1d35d1c40289bad465978750ba738acf28c90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212443"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="e3b7b-102">StrongNameSignatureVerificationFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e3b7b-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="e3b7b-103">Sprawdza, czy zestaw, który został już zmapowany do pamięci jest prawidłowa dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="e3b7b-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-104">This function has been deprecated.</span></span> <span data-ttu-id="e3b7b-105">Użyj [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b7b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3b7b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3b7b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3b7b-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="e3b7b-108">[in] Względna wirtualny adres manifestu zestawu zamapowany.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e3b7b-109">[in] Rozmiar w bajtach zamapowanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="e3b7b-110">[in] Flagi, które wpływają na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="e3b7b-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="e3b7b-111">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="e3b7b-112">(0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-112">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="e3b7b-113">(0x00000002) — określa, że jest pierwszej weryfikacji wykonywane w tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-113">(0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="e3b7b-114">(0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-114">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="e3b7b-115">(0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-115">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="e3b7b-116">(0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-116">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="e3b7b-117">(0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-117">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="e3b7b-118">[out] Flaga informacji dodatkowych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="e3b7b-119">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="e3b7b-119">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="e3b7b-120">(0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-120">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3b7b-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e3b7b-121">Return Value</span></span>  
 `true` <span data-ttu-id="e3b7b-122">Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-122">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3b7b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3b7b-123">Remarks</span></span>  
 <span data-ttu-id="e3b7b-124">Jeśli `StrongNameSignatureVerificationFromImage` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e3b7b-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3b7b-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3b7b-125">Requirements</span></span>  
 <span data-ttu-id="e3b7b-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3b7b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3b7b-127">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e3b7b-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e3b7b-128">**Biblioteka:** Dołączony jako zasób w mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e3b7b-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="e3b7b-129">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e3b7b-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3b7b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3b7b-130">See also</span></span>

- [<span data-ttu-id="e3b7b-131">StrongNameSignatureVerificationFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="e3b7b-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="e3b7b-132">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e3b7b-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
