---
title: "StrongNameGetBlobFromImage — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 423f874796320d1fbcda2ab642c71b7072642569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="a6b2b-102">StrongNameGetBlobFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a6b2b-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="a6b2b-103">Pobiera zestawu obraz to binarna reprezentacja pod adresem określonym pamięci.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="a6b2b-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-104">This function has been deprecated.</span></span> <span data-ttu-id="a6b2b-105">Użyj [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b2b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6b2b-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6b2b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6b2b-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="a6b2b-108">[in] Adres pamięci manifest zestawu mapowane.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a6b2b-109">[in] Rozmiar w bajtach obrazu w `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="a6b2b-110">[in] Bufor zawiera binarna reprezentacja obrazu.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="a6b2b-111">[w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="a6b2b-112">Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6b2b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a6b2b-113">Return Value</span></span>  
 <span data-ttu-id="a6b2b-114">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6b2b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6b2b-115">Remarks</span></span>  
 <span data-ttu-id="a6b2b-116">Jeśli `StrongNameGetBlobFromImage` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="a6b2b-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6b2b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6b2b-117">Requirements</span></span>  
 <span data-ttu-id="a6b2b-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6b2b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6b2b-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a6b2b-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a6b2b-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6b2b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6b2b-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6b2b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b2b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6b2b-122">See Also</span></span>  
 [<span data-ttu-id="a6b2b-123">StrongNameGetBlobFromImage — metoda</span><span class="sxs-lookup"><span data-stu-id="a6b2b-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="a6b2b-124">StrongNameGetBlob — metoda</span><span class="sxs-lookup"><span data-stu-id="a6b2b-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="a6b2b-125">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="a6b2b-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
