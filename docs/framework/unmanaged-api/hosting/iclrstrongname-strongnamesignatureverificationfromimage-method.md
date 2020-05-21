---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 1ba7355fae1888436d57562cc21d3865ebc7a4f4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763179"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="ee766-102">ICLRStrongName::StrongNameSignatureVerificationFromImage — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee766-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="ee766-103">Sprawdza, czy zestaw, który został już zamapowany na pamięć, jest prawidłowy dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ee766-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee766-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee766-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee766-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee766-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="ee766-106">podczas Względny adres wirtualny zamapowanego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="ee766-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ee766-107">podczas Rozmiar zamapowanego obrazu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="ee766-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="ee766-108">podczas Flagi wpływające na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="ee766-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="ee766-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ee766-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="ee766-110">`SN_INFLAG_FORCE_VER`(0x00000001) — wymusza weryfikację, nawet jeśli konieczne jest przesłonięcie ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="ee766-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="ee766-111">`SN_INFLAG_INSTALL`(0x00000002) — określa, że jest to pierwsza weryfikacja wykonywana na tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="ee766-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="ee766-112">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) — określa, że pamięć podręczna będzie zezwalać na dostęp tylko użytkownikom z uprawnieniami administracyjnymi.</span><span class="sxs-lookup"><span data-stu-id="ee766-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="ee766-113">`SN_INFLAG_USER_ACCESS`(0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ee766-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="ee766-114">`SN_INFLAG_ALL_ACCESS`(0x00000010) — określa, że pamięć podręczna nie będzie zapewniać żadnych gwarancji ograniczenia dostępu.</span><span class="sxs-lookup"><span data-stu-id="ee766-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="ee766-115">`SN_INFLAG_RUNTIME`(0x80000000) — zarezerwowane do debugowania wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="ee766-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="ee766-116">określoną Flaga dodatkowych informacji wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="ee766-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="ee766-117">Obsługiwana jest następująca wartość:</span><span class="sxs-lookup"><span data-stu-id="ee766-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="ee766-118">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) — ta wartość jest ustawiona na `false` , aby określić, że weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="ee766-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee766-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ee766-119">Return Value</span></span>  
 <span data-ttu-id="ee766-120">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="ee766-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee766-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee766-121">Requirements</span></span>  
 <span data-ttu-id="ee766-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee766-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee766-123">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="ee766-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee766-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ee766-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee766-125">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee766-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee766-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee766-126">See also</span></span>

- [<span data-ttu-id="ee766-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee766-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
