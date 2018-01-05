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
ms.workload: dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="1aaf3-102">StrongNameGetBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="1aaf3-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="1aaf3-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="1aaf3-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-104">This function has been deprecated.</span></span> <span data-ttu-id="1aaf3-105">Użyj [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aaf3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1aaf3-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1aaf3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="1aaf3-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="1aaf3-108">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="1aaf3-109">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="1aaf3-110">[w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="1aaf3-111">Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1aaf3-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1aaf3-112">Return Value</span></span>  
 <span data-ttu-id="1aaf3-113">`true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aaf3-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1aaf3-114">Remarks</span></span>  
 <span data-ttu-id="1aaf3-115">Jeśli `StrongNameGetBlob` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="1aaf3-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aaf3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1aaf3-116">Requirements</span></span>  
 <span data-ttu-id="1aaf3-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aaf3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aaf3-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="1aaf3-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1aaf3-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1aaf3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1aaf3-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aaf3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aaf3-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1aaf3-121">See Also</span></span>  
 [<span data-ttu-id="1aaf3-122">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="1aaf3-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="1aaf3-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="1aaf3-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="1aaf3-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="1aaf3-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
