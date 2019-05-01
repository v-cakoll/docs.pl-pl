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
ms.openlocfilehash: 412aa8fd30294ac9681a5edd02bb4bdfe25b3fab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993060"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="06a60-102">ICLRStrongName::StrongNameKeyDelete — Metoda</span><span class="sxs-lookup"><span data-stu-id="06a60-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="06a60-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="06a60-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06a60-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06a60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06a60-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="06a60-106">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="06a60-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06a60-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="06a60-107">Return Value</span></span>  
 <span data-ttu-id="06a60-108">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="06a60-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06a60-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06a60-109">Remarks</span></span>  
 <span data-ttu-id="06a60-110">Użyj [iclrstrongname::strongnamekeyinstall —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metodę, aby zaimportować pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="06a60-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06a60-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06a60-111">Requirements</span></span>  
 <span data-ttu-id="06a60-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06a60-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06a60-113">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="06a60-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="06a60-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06a60-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06a60-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06a60-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a60-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06a60-116">See also</span></span>

- [<span data-ttu-id="06a60-117">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="06a60-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="06a60-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="06a60-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
