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
ms.openlocfilehash: 8f6f2445d88d608d51be4e6fe1e064efbb58325d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763101"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="910e7-102">ICLRStrongName::StrongNameKeyDelete — Metoda</span><span class="sxs-lookup"><span data-stu-id="910e7-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="910e7-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="910e7-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="910e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="910e7-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="910e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="910e7-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="910e7-106">podczas Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="910e7-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="910e7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="910e7-107">Return Value</span></span>  
 <span data-ttu-id="910e7-108">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="910e7-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="910e7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="910e7-109">Remarks</span></span>  
 <span data-ttu-id="910e7-110">Użyj metody [ICLRStrongName:: StrongNameKeyInstall —](iclrstrongname-strongnamekeyinstall-method.md) w celu zaimportowania pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="910e7-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="910e7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="910e7-111">Requirements</span></span>  
 <span data-ttu-id="910e7-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="910e7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="910e7-113">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="910e7-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="910e7-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="910e7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="910e7-115">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="910e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910e7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="910e7-116">See also</span></span>

- [<span data-ttu-id="910e7-117">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="910e7-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="910e7-118">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="910e7-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
