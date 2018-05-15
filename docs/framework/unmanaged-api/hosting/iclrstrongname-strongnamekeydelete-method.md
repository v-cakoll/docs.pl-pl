---
title: ICLRStrongName::StrongNameKeyDelete — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9cd423bd351d9e4b12f21fe3a4a52c9909b7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="5e465-102">ICLRStrongName::StrongNameKeyDelete — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e465-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="5e465-103">Usuwa określony kontener klucza.</span><span class="sxs-lookup"><span data-stu-id="5e465-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e465-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e465-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="5e465-106">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="5e465-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e465-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e465-107">Return Value</span></span>  
 <span data-ttu-id="5e465-108">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="5e465-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e465-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e465-109">Remarks</span></span>  
 <span data-ttu-id="5e465-110">Użyj [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metodę, aby zaimportować pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="5e465-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e465-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e465-111">Requirements</span></span>  
 <span data-ttu-id="5e465-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e465-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e465-113">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5e465-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e465-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e465-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e465-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e465-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e465-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e465-116">See Also</span></span>  
 [<span data-ttu-id="5e465-117">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="5e465-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="5e465-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e465-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
