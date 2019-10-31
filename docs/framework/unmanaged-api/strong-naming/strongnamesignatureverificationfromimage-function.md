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
ms.openlocfilehash: 5c12ca20deee06fcaca68365644fd9dff95379ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121162"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="bf5ba-102">StrongNameSignatureVerificationFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="bf5ba-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="bf5ba-103">Sprawdza, czy zestaw, który został już zamapowany na pamięć, jest prawidłowy dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="bf5ba-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-104">This function has been deprecated.</span></span> <span data-ttu-id="bf5ba-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf5ba-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf5ba-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf5ba-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf5ba-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf5ba-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="bf5ba-108">podczas Względny adres wirtualny zamapowanego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="bf5ba-109">podczas Rozmiar zamapowanego obrazu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="bf5ba-110">podczas Flagi wpływające na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="bf5ba-111">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="bf5ba-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="bf5ba-112">`SN_INFLAG_FORCE_VER` (0x00000001) — wymusza weryfikację, nawet jeśli jest konieczna przesłonięcie ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="bf5ba-113">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest to pierwsza weryfikacja wykonywana na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="bf5ba-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna będzie zezwalać na dostęp tylko użytkownikom z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="bf5ba-115">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="bf5ba-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna nie będzie zapewniać żadnych gwarancji ograniczenia dostępu.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="bf5ba-117">`SN_INFLAG_RUNTIME` (0x80000000) — zarezerwowane na potrzeby debugowania wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="bf5ba-118">określoną Flaga dodatkowych informacji wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="bf5ba-119">Obsługiwana jest następująca wartość:</span><span class="sxs-lookup"><span data-stu-id="bf5ba-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="bf5ba-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest ustawiona na `false`, aby określić, że weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf5ba-121">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf5ba-121">Return Value</span></span>  
 <span data-ttu-id="bf5ba-122">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf5ba-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf5ba-123">Remarks</span></span>  
 <span data-ttu-id="bf5ba-124">Jeśli funkcja `StrongNameSignatureVerificationFromImage` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="bf5ba-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf5ba-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf5ba-125">Requirements</span></span>  
 <span data-ttu-id="bf5ba-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf5ba-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf5ba-127">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bf5ba-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bf5ba-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bf5ba-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="bf5ba-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5ba-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5ba-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf5ba-130">See also</span></span>

- [<span data-ttu-id="bf5ba-131">StrongNameSignatureVerificationFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="bf5ba-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="bf5ba-132">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf5ba-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
