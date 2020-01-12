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
ms.openlocfilehash: 2a76377857c3cf1e40a328b9a13fb4834321707e
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899566"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="20550-102">ICLRStrongName::StrongNameKeyInstall — Metoda</span><span class="sxs-lookup"><span data-stu-id="20550-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="20550-103">Importuje parę kluczy publiczny/prywatny do kontenera.</span><span class="sxs-lookup"><span data-stu-id="20550-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20550-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20550-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20550-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20550-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="20550-106">podczas Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="20550-106">[in] The name of the key container.</span></span> <span data-ttu-id="20550-107">`wszKeyContainer` musi być niepustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="20550-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="20550-108">podczas Para kluczy binarnych.</span><span class="sxs-lookup"><span data-stu-id="20550-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="20550-109">podczas Rozmiar w bajtach `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="20550-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20550-110">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="20550-110">Return Value</span></span>  
 <span data-ttu-id="20550-111">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="20550-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20550-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20550-112">Remarks</span></span>  
 <span data-ttu-id="20550-113">Aby usunąć kontener kluczy, użyj metody [ICLRStrongName:: StrongNameKeyDelete —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="20550-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20550-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20550-114">Requirements</span></span>  
 <span data-ttu-id="20550-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20550-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20550-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="20550-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20550-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20550-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20550-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20550-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20550-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20550-119">See also</span></span>

- [<span data-ttu-id="20550-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="20550-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="20550-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="20550-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
