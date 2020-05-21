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
ms.openlocfilehash: e0c60d6e74c48531a223f6dbb35125b5a2017cbb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763046"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="7fa5a-102">ICLRStrongName::StrongNameKeyInstall — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fa5a-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="7fa5a-103">Importuje parę kluczy publiczny/prywatny do kontenera.</span><span class="sxs-lookup"><span data-stu-id="7fa5a-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fa5a-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fa5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fa5a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="7fa5a-106">podczas Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="7fa5a-106">[in] The name of the key container.</span></span> <span data-ttu-id="7fa5a-107">`wszKeyContainer`nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="7fa5a-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="7fa5a-108">podczas Para kluczy binarnych.</span><span class="sxs-lookup"><span data-stu-id="7fa5a-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="7fa5a-109">podczas Rozmiar, w bajtach, z `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="7fa5a-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fa5a-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7fa5a-110">Return Value</span></span>  
 <span data-ttu-id="7fa5a-111">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7fa5a-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fa5a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fa5a-112">Remarks</span></span>  
 <span data-ttu-id="7fa5a-113">Aby usunąć kontener kluczy, użyj metody [ICLRStrongName:: StrongNameKeyDelete —](iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7fa5a-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fa5a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fa5a-114">Requirements</span></span>  
 <span data-ttu-id="7fa5a-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fa5a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fa5a-116">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="7fa5a-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7fa5a-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7fa5a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fa5a-118">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fa5a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fa5a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fa5a-119">See also</span></span>

- [<span data-ttu-id="7fa5a-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="7fa5a-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="7fa5a-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7fa5a-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
