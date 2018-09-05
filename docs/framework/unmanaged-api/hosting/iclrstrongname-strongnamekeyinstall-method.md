---
title: ICLRStrongName::StrongNameKeyInstall — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d60e1e503cd48b9b9e2ed91a6bfea000aeeea2af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527879"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="31300-102">ICLRStrongName::StrongNameKeyInstall — Metoda</span><span class="sxs-lookup"><span data-stu-id="31300-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="31300-103">Importuje pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="31300-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31300-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31300-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31300-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31300-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="31300-106">[in] Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="31300-106">[in] The name of the key container.</span></span> <span data-ttu-id="31300-107">`wszKeyContainer` musi być ciągiem niepustym.</span><span class="sxs-lookup"><span data-stu-id="31300-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="31300-108">[in] Binarny pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="31300-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="31300-109">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="31300-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31300-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="31300-110">Return Value</span></span>  
 <span data-ttu-id="31300-111">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="31300-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31300-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31300-112">Remarks</span></span>  
 <span data-ttu-id="31300-113">Użyj [iclrstrongname::strongnamekeydelete —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metodę, aby usunąć kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="31300-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31300-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31300-114">Requirements</span></span>  
 <span data-ttu-id="31300-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31300-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31300-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="31300-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="31300-117">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31300-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31300-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31300-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31300-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31300-119">See Also</span></span>  
 [<span data-ttu-id="31300-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="31300-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="31300-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="31300-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
