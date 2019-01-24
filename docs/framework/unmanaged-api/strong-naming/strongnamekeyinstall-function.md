---
title: StrongNameKeyInstall — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecd52fce8033876f0599fa0ba25fae0850c0e01f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508493"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="69fba-102">StrongNameKeyInstall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="69fba-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="69fba-103">Importuje pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="69fba-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="69fba-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="69fba-104">This function has been deprecated.</span></span> <span data-ttu-id="69fba-105">Użyj [iclrstrongname::strongnamekeyinstall —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="69fba-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69fba-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="69fba-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69fba-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="69fba-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="69fba-108">[in] Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="69fba-108">[in] The name of the key container.</span></span> <span data-ttu-id="69fba-109">`wszKeyContainer` musi być ciągiem niepustym.</span><span class="sxs-lookup"><span data-stu-id="69fba-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="69fba-110">[in] Binarny pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="69fba-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="69fba-111">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="69fba-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69fba-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69fba-112">Return Value</span></span>  
 <span data-ttu-id="69fba-113">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="69fba-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69fba-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69fba-114">Remarks</span></span>  
 <span data-ttu-id="69fba-115">Użyj [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) funkcję, aby usunąć kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="69fba-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="69fba-116">Jeśli `StrongNameKeyInstall` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="69fba-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69fba-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69fba-117">Requirements</span></span>  
 <span data-ttu-id="69fba-118">**Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69fba-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69fba-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="69fba-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="69fba-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69fba-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69fba-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69fba-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69fba-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69fba-122">See also</span></span>
- [<span data-ttu-id="69fba-123">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="69fba-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="69fba-124">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="69fba-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="69fba-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="69fba-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
