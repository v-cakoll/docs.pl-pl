---
title: "StrongNameKeyInstall — Funkcja"
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
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a8dbc84f375b7bbbad47971936650d81c5c63df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="d1a26-102">StrongNameKeyInstall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d1a26-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="d1a26-103">Importuje pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="d1a26-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="d1a26-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d1a26-104">This function has been deprecated.</span></span> <span data-ttu-id="d1a26-105">Użyj [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d1a26-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1a26-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1a26-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1a26-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1a26-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="d1a26-108">[in] Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="d1a26-108">[in] The name of the key container.</span></span> <span data-ttu-id="d1a26-109">`wszKeyContainer`musi być niepustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="d1a26-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d1a26-110">[in] Binarny pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="d1a26-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d1a26-111">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="d1a26-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1a26-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1a26-112">Return Value</span></span>  
 <span data-ttu-id="d1a26-113">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d1a26-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1a26-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1a26-114">Remarks</span></span>  
 <span data-ttu-id="d1a26-115">Użyj [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) funkcji można usunąć kontenera klucza.</span><span class="sxs-lookup"><span data-stu-id="d1a26-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="d1a26-116">Jeśli `StrongNameKeyInstall` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="d1a26-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a26-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1a26-117">Requirements</span></span>  
 <span data-ttu-id="d1a26-118">**Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1a26-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a26-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d1a26-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d1a26-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1a26-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1a26-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a26-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a26-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1a26-122">See Also</span></span>  
 [<span data-ttu-id="d1a26-123">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="d1a26-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="d1a26-124">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="d1a26-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="d1a26-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1a26-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
