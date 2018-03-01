---
title: "ICLRStrongName::StrongNameKeyInstall — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df1bdb5d6d6018855cb76b48d58e557a61288a51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="bbdc8-102">ICLRStrongName::StrongNameKeyInstall — Metoda</span><span class="sxs-lookup"><span data-stu-id="bbdc8-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="bbdc8-103">Importuje pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbdc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbdc8-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbdc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbdc8-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="bbdc8-106">[in] Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-106">[in] The name of the key container.</span></span> <span data-ttu-id="bbdc8-107">`wszKeyContainer`musi być niepustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="bbdc8-108">[in] Binarny pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="bbdc8-109">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbdc8-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bbdc8-110">Return Value</span></span>  
 <span data-ttu-id="bbdc8-111">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="bbdc8-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbdc8-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbdc8-112">Remarks</span></span>  
 <span data-ttu-id="bbdc8-113">Użyj [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metody można usunąć kontenera klucza.</span><span class="sxs-lookup"><span data-stu-id="bbdc8-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdc8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbdc8-114">Requirements</span></span>  
 <span data-ttu-id="bbdc8-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbdc8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdc8-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bbdc8-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bbdc8-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bbdc8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbdc8-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdc8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdc8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbdc8-119">See Also</span></span>  
 [<span data-ttu-id="bbdc8-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="bbdc8-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="bbdc8-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="bbdc8-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
