---
title: "StrongNameKeyDelete — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c7b3ccc9ec1b8cbc81de115f734e1d11e0e0ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="0941d-102">StrongNameKeyDelete — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0941d-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="0941d-103">Usuwa określony kontener klucza.</span><span class="sxs-lookup"><span data-stu-id="0941d-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="0941d-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="0941d-104">This function has been deprecated.</span></span> <span data-ttu-id="0941d-105">Użyj [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="0941d-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0941d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0941d-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0941d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0941d-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="0941d-108">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="0941d-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0941d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0941d-109">Return Value</span></span>  
 <span data-ttu-id="0941d-110">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="0941d-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0941d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0941d-111">Remarks</span></span>  
 <span data-ttu-id="0941d-112">Użyj [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) funkcja importa pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="0941d-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="0941d-113">Jeśli `StrongNameKeyDelete` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="0941d-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0941d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0941d-114">Requirements</span></span>  
 <span data-ttu-id="0941d-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0941d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0941d-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0941d-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0941d-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0941d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0941d-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0941d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0941d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0941d-119">See Also</span></span>  
 [<span data-ttu-id="0941d-120">StrongNameKeyDelete — metoda</span><span class="sxs-lookup"><span data-stu-id="0941d-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="0941d-121">StrongNameKeyInstall — metoda</span><span class="sxs-lookup"><span data-stu-id="0941d-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="0941d-122">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="0941d-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
