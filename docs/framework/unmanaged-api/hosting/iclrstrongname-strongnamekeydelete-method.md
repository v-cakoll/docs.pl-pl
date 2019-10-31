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
ms.openlocfilehash: 4e72818be6808c519677192d3744bbc5ec414d0d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135082"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="4e8e4-102">ICLRStrongName::StrongNameKeyDelete — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e8e4-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="4e8e4-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="4e8e4-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e8e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e8e4-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e8e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e8e4-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4e8e4-106">podczas Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="4e8e4-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e8e4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e8e4-107">Return Value</span></span>  
 <span data-ttu-id="4e8e4-108">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="4e8e4-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e8e4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e8e4-109">Remarks</span></span>  
 <span data-ttu-id="4e8e4-110">Użyj metody [ICLRStrongName:: StrongNameKeyInstall —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) w celu zaimportowania pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="4e8e4-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e8e4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e8e4-111">Requirements</span></span>  
 <span data-ttu-id="4e8e4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e8e4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e8e4-113">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="4e8e4-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4e8e4-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e8e4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e8e4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e8e4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e8e4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e8e4-116">See also</span></span>

- [<span data-ttu-id="4e8e4-117">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="4e8e4-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="4e8e4-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e8e4-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
