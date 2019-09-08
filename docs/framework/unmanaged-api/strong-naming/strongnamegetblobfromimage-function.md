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
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799087"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="a9c95-102">StrongNameGetBlobFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a9c95-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="a9c95-103">Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.</span><span class="sxs-lookup"><span data-stu-id="a9c95-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="a9c95-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a9c95-104">This function has been deprecated.</span></span> <span data-ttu-id="a9c95-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetBlobFromImage —](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a9c95-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9c95-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9c95-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9c95-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9c95-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="a9c95-108">podczas Adres pamięci mapowanego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="a9c95-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="a9c95-109">podczas Rozmiar obrazu `pbBase`w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a9c95-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="a9c95-110">podczas Bufor zawierający reprezentację binarną obrazu.</span><span class="sxs-lookup"><span data-stu-id="a9c95-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="a9c95-111">[in. out] Żądany maksymalny rozmiar, w bajtach, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="a9c95-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="a9c95-112">Po powrocie, rzeczywisty rozmiar, w bajtach, `pbBlob`z.</span><span class="sxs-lookup"><span data-stu-id="a9c95-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9c95-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a9c95-113">Return Value</span></span>  
 <span data-ttu-id="a9c95-114">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="a9c95-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9c95-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9c95-115">Remarks</span></span>  
 <span data-ttu-id="a9c95-116">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameGetBlobFromImage`</span><span class="sxs-lookup"><span data-stu-id="a9c95-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9c95-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9c95-117">Requirements</span></span>  
 <span data-ttu-id="a9c95-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9c95-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9c95-119">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a9c95-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a9c95-120">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a9c95-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9c95-121">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9c95-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9c95-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9c95-122">See also</span></span>

- [<span data-ttu-id="a9c95-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="a9c95-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="a9c95-124">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="a9c95-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="a9c95-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9c95-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
