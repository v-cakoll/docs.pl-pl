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
ms.openlocfilehash: 693a5831934647256ac48c8f3a2d30325dee4349
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135039"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="99c86-102">ICLRStrongName::StrongNameKeyInstall — Metoda</span><span class="sxs-lookup"><span data-stu-id="99c86-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="99c86-103">Importuje parę kluczy publiczny/prywatny do kontenera.</span><span class="sxs-lookup"><span data-stu-id="99c86-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c86-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="99c86-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99c86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99c86-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="99c86-106">podczas Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="99c86-106">[in] The name of the key container.</span></span> <span data-ttu-id="99c86-107">`wszKeyContainer` musi być niepustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="99c86-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="99c86-108">podczas Para kluczy binarnych.</span><span class="sxs-lookup"><span data-stu-id="99c86-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="99c86-109">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="99c86-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99c86-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="99c86-110">Return Value</span></span>  
 <span data-ttu-id="99c86-111">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="99c86-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99c86-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99c86-112">Remarks</span></span>  
 <span data-ttu-id="99c86-113">Aby usunąć kontener kluczy, użyj metody [ICLRStrongName:: StrongNameKeyDelete —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99c86-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c86-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99c86-114">Requirements</span></span>  
 <span data-ttu-id="99c86-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99c86-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99c86-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="99c86-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="99c86-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99c86-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99c86-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99c86-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c86-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99c86-119">See also</span></span>

- [<span data-ttu-id="99c86-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="99c86-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="99c86-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="99c86-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
