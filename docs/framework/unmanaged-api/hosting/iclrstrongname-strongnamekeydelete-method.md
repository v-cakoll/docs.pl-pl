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
ms.openlocfilehash: 95098cbb060c06d2d5a5a4c04b6fa9017bca66a1
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899595"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="db1b5-102">ICLRStrongName::StrongNameKeyDelete — Metoda</span><span class="sxs-lookup"><span data-stu-id="db1b5-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="db1b5-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="db1b5-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db1b5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db1b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db1b5-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="db1b5-106">podczas Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="db1b5-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db1b5-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="db1b5-107">Return Value</span></span>  
 <span data-ttu-id="db1b5-108">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="db1b5-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db1b5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db1b5-109">Remarks</span></span>  
 <span data-ttu-id="db1b5-110">Użyj metody [ICLRStrongName:: StrongNameKeyInstall —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) w celu zaimportowania pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="db1b5-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db1b5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db1b5-111">Requirements</span></span>  
 <span data-ttu-id="db1b5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db1b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db1b5-113">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="db1b5-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db1b5-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db1b5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db1b5-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db1b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1b5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db1b5-116">See also</span></span>

- [<span data-ttu-id="db1b5-117">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="db1b5-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="db1b5-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="db1b5-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
