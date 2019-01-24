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
ms.openlocfilehash: 3eace88e5034c61b7608a6d777608cc2544b8564
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688483"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="54e34-102">StrongNameKeyDelete — Funkcja</span><span class="sxs-lookup"><span data-stu-id="54e34-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="54e34-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="54e34-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="54e34-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="54e34-104">This function has been deprecated.</span></span> <span data-ttu-id="54e34-105">Użyj [iclrstrongname::strongnamekeydelete —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="54e34-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e34-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="54e34-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54e34-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="54e34-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="54e34-108">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="54e34-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54e34-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="54e34-109">Return Value</span></span>  
 <span data-ttu-id="54e34-110">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="54e34-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54e34-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54e34-111">Remarks</span></span>  
 <span data-ttu-id="54e34-112">Użyj [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) funkcji importa pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="54e34-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="54e34-113">Jeśli `StrongNameKeyDelete` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="54e34-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54e34-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54e34-114">Requirements</span></span>  
 <span data-ttu-id="54e34-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54e34-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54e34-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="54e34-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="54e34-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54e34-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54e34-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54e34-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e34-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54e34-119">See also</span></span>
- [<span data-ttu-id="54e34-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="54e34-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="54e34-121">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="54e34-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="54e34-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="54e34-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
