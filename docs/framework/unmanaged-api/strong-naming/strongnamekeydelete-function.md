---
title: StrongNameKeyDelete — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a35ec4e3c3110616ac20cd31db134371838deda0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="473a7-102">StrongNameKeyDelete — Funkcja</span><span class="sxs-lookup"><span data-stu-id="473a7-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="473a7-103">Usuwa określony kontener klucza.</span><span class="sxs-lookup"><span data-stu-id="473a7-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="473a7-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="473a7-104">This function has been deprecated.</span></span> <span data-ttu-id="473a7-105">Użyj [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="473a7-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="473a7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="473a7-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="473a7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="473a7-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="473a7-108">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="473a7-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="473a7-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="473a7-109">Return Value</span></span>  
 <span data-ttu-id="473a7-110">`true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="473a7-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="473a7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="473a7-111">Remarks</span></span>  
 <span data-ttu-id="473a7-112">Użyj [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) funkcja importa pary kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="473a7-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="473a7-113">Jeśli `StrongNameKeyDelete` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="473a7-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473a7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="473a7-114">Requirements</span></span>  
 <span data-ttu-id="473a7-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="473a7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473a7-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="473a7-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="473a7-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="473a7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="473a7-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473a7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473a7-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="473a7-119">See Also</span></span>  
 [<span data-ttu-id="473a7-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="473a7-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="473a7-121">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="473a7-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="473a7-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="473a7-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
