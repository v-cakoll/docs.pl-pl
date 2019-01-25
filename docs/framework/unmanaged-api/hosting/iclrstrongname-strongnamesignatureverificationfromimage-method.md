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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c2151494a2ddfc200edc9c6c6cc3f7639bcf19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728885"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="47346-102">ICLRStrongName::StrongNameSignatureVerificationFromImage — Metoda</span><span class="sxs-lookup"><span data-stu-id="47346-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="47346-103">Sprawdza, czy zestaw, który został już zmapowany do pamięci jest prawidłowa dla skojarzonego klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="47346-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47346-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47346-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47346-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47346-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="47346-106">[in] Względna wirtualny adres manifestu zestawu zamapowany.</span><span class="sxs-lookup"><span data-stu-id="47346-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="47346-107">[in] Rozmiar w bajtach zamapowanego obrazu.</span><span class="sxs-lookup"><span data-stu-id="47346-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="47346-108">[in] Flagi, które wpływają na zachowanie weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="47346-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="47346-109">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="47346-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="47346-110">`SN_INFLAG_FORCE_VER` (0x00000001) - wymusza weryfikację, nawet jeśli jest zastąpić ustawienia rejestru.</span><span class="sxs-lookup"><span data-stu-id="47346-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="47346-111">`SN_INFLAG_INSTALL` (0x00000002) — określa, że jest pierwszej weryfikacji wykonywane w tym obrazie.</span><span class="sxs-lookup"><span data-stu-id="47346-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="47346-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) — określa, że pamięć podręczna zezwoli na dostęp tylko do użytkowników, którzy mają uprawnienia administracyjne.</span><span class="sxs-lookup"><span data-stu-id="47346-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="47346-113">`SN_INFLAG_USER_ACCESS` (0x00000008) — określa, że zestaw będzie dostępny tylko dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="47346-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="47346-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) — określa, że pamięć podręczna zapewni żadnych gwarancji ograniczenie dostępu.</span><span class="sxs-lookup"><span data-stu-id="47346-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="47346-115">`SN_INFLAG_RUNTIME` (0x80000000) - zarezerwowane dla wewnętrznego debugowania.</span><span class="sxs-lookup"><span data-stu-id="47346-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="47346-116">[out] Flaga informacji dodatkowych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="47346-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="47346-117">Obsługiwane jest następującą wartość:</span><span class="sxs-lookup"><span data-stu-id="47346-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="47346-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) — ta wartość jest równa `false` do określenia, czy Weryfikacja powiodła się z powodu ustawień rejestru.</span><span class="sxs-lookup"><span data-stu-id="47346-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47346-119">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="47346-119">Return Value</span></span>  
 <span data-ttu-id="47346-120">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="47346-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47346-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47346-121">Requirements</span></span>  
 <span data-ttu-id="47346-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47346-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47346-123">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="47346-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="47346-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47346-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47346-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47346-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47346-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47346-126">See also</span></span>
- [<span data-ttu-id="47346-127">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="47346-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
