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
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798950"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="af016-102">StrongNameSignatureVerification — Funkcja</span><span class="sxs-lookup"><span data-stu-id="af016-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="af016-103">Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera sygnaturę silnej nazwy, która jest sprawdzana według określonych flag.</span><span class="sxs-lookup"><span data-stu-id="af016-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="af016-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="af016-104">This function has been deprecated.</span></span> <span data-ttu-id="af016-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureVerification —](../hosting/iclrstrongname-strongnamesignatureverification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af016-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af016-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="af016-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af016-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="af016-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="af016-108">podczas Ścieżka do przenośnego pliku wykonywalnego (. dll lub. exe) dla zestawu do zweryfikowania.</span><span class="sxs-lookup"><span data-stu-id="af016-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="af016-109">podczas Flagi modyfikujące zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="af016-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="af016-110">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="af016-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="af016-111">`SN_INFLAG_FORCE_VER`(0x00000001) — wymusza weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="af016-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="af016-112">`SN_INFLAG_INSTALL`(0x00000002) — określa, że jest to pierwsze sprawdzenie manifestu.</span><span class="sxs-lookup"><span data-stu-id="af016-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="af016-113">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) — określa, że pamięć podręczna będzie zezwalać na dostęp tylko użytkownikom z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="af016-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="af016-114">`SN_INFLAG_USER_ACCESS`(0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="af016-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="af016-115">`SN_INFLAG_ALL_ACCESS`(0x00000010) — określa, że pamięć podręczna nie będzie zapewniać żadnych gwarancji ograniczenia dostępu.</span><span class="sxs-lookup"><span data-stu-id="af016-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="af016-116">`SN_INFLAG_RUNTIME`(0x80000000) — zarezerwowane do debugowania wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="af016-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="af016-117">określoną Flagi wskazujące, czy podpis silnej nazwy został zweryfikowany.</span><span class="sxs-lookup"><span data-stu-id="af016-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="af016-118">Obsługiwana jest następująca wartość:</span><span class="sxs-lookup"><span data-stu-id="af016-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="af016-119">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) — ta wartość jest ustawiona na `false` , aby określić, że weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="af016-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af016-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="af016-120">Return Value</span></span>  
 <span data-ttu-id="af016-121">`true`Jeśli weryfikacja zakończyła się pomyślnie; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="af016-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af016-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af016-122">Requirements</span></span>  
 <span data-ttu-id="af016-123">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af016-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af016-124">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="af016-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="af016-125">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af016-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af016-126">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af016-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af016-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af016-127">See also</span></span>

- [<span data-ttu-id="af016-128">StrongNameSignatureVerification, metoda</span><span class="sxs-lookup"><span data-stu-id="af016-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="af016-129">StrongNameSignatureVerificationEx, metoda</span><span class="sxs-lookup"><span data-stu-id="af016-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="af016-130">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="af016-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
