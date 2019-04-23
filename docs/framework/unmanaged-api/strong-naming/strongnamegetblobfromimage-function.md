---
title: StrongNameGetBlobFromImage — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b136e1fa480e53bcacfd9ea832d1dc4d1bd69f74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162784"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="f57d5-102">StrongNameGetBlobFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f57d5-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="f57d5-103">Pobiera reprezentacja binarna obrazu zestawu pod adresem określonym pamięci.</span><span class="sxs-lookup"><span data-stu-id="f57d5-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="f57d5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f57d5-104">This function has been deprecated.</span></span> <span data-ttu-id="f57d5-105">Użyj [iclrstrongname::strongnamegetblobfromimage —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="f57d5-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57d5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f57d5-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f57d5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f57d5-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="f57d5-108">[in] Adres pamięci manifestu zestawu zamapowany.</span><span class="sxs-lookup"><span data-stu-id="f57d5-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="f57d5-109">[in] Rozmiar w bajtach, obraz u `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="f57d5-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="f57d5-110">[in] Bufor do przechowywania reprezentacja binarna obrazu.</span><span class="sxs-lookup"><span data-stu-id="f57d5-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="f57d5-111">[out w] Maksymalny rozmiar w bajtach, żądane `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f57d5-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="f57d5-112">Po powrocie, rzeczywisty rozmiar w bajtach, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f57d5-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f57d5-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f57d5-113">Return Value</span></span>  
 <span data-ttu-id="f57d5-114">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="f57d5-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f57d5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f57d5-115">Remarks</span></span>  
 <span data-ttu-id="f57d5-116">Jeśli `StrongNameGetBlobFromImage` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="f57d5-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f57d5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f57d5-117">Requirements</span></span>  
 <span data-ttu-id="f57d5-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f57d5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57d5-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f57d5-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f57d5-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f57d5-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f57d5-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f57d5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57d5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f57d5-122">See also</span></span>

- [<span data-ttu-id="f57d5-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="f57d5-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="f57d5-124">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="f57d5-124">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="f57d5-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f57d5-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
