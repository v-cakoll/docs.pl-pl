---
title: "StrongNameGetBlob — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="723a5-102">StrongNameGetBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="723a5-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="723a5-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="723a5-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="723a5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="723a5-104">This function has been deprecated.</span></span> <span data-ttu-id="723a5-105">Użyj [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="723a5-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723a5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="723a5-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="723a5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="723a5-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="723a5-108">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="723a5-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="723a5-109">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="723a5-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="723a5-110">[w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="723a5-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="723a5-111">Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="723a5-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="723a5-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="723a5-112">Return Value</span></span>  
 <span data-ttu-id="723a5-113">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="723a5-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="723a5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="723a5-114">Remarks</span></span>  
 <span data-ttu-id="723a5-115">Jeśli `StrongNameGetBlob` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="723a5-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="723a5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="723a5-116">Requirements</span></span>  
 <span data-ttu-id="723a5-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="723a5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723a5-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="723a5-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="723a5-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="723a5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="723a5-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723a5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723a5-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="723a5-121">See Also</span></span>  
 [<span data-ttu-id="723a5-122">StrongNameGetBlob — metoda</span><span class="sxs-lookup"><span data-stu-id="723a5-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="723a5-123">StrongNameGetBlobFromImage — metoda</span><span class="sxs-lookup"><span data-stu-id="723a5-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="723a5-124">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="723a5-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
