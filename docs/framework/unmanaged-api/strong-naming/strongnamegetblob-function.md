---
title: StrongNameGetBlob — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e23232b55a841672ee193b980c310995ba688e00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049365"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="72135-102">StrongNameGetBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="72135-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="72135-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="72135-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="72135-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="72135-104">This function has been deprecated.</span></span> <span data-ttu-id="72135-105">Użyj [iclrstrongname::strongnamegetblob —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="72135-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72135-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="72135-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72135-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="72135-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="72135-108">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="72135-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="72135-109">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="72135-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="72135-110">[out w] Maksymalny rozmiar w bajtach, żądane `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="72135-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="72135-111">Po powrocie, rzeczywisty rozmiar w bajtach, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="72135-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72135-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="72135-112">Return Value</span></span>  
 <span data-ttu-id="72135-113">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="72135-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72135-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72135-114">Remarks</span></span>  
 <span data-ttu-id="72135-115">Jeśli `StrongNameGetBlob` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="72135-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72135-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72135-116">Requirements</span></span>  
 <span data-ttu-id="72135-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72135-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72135-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="72135-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72135-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72135-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72135-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72135-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72135-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72135-121">See also</span></span>

- [<span data-ttu-id="72135-122">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="72135-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="72135-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="72135-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="72135-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="72135-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
