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
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094880"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="48e0b-102">StrongNameGetBlobFromImage — Funkcja</span><span class="sxs-lookup"><span data-stu-id="48e0b-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="48e0b-103">Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.</span><span class="sxs-lookup"><span data-stu-id="48e0b-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="48e0b-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="48e0b-104">This function has been deprecated.</span></span> <span data-ttu-id="48e0b-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetBlobFromImage —](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .</span><span class="sxs-lookup"><span data-stu-id="48e0b-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e0b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="48e0b-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48e0b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="48e0b-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="48e0b-108">podczas Adres pamięci mapowanego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="48e0b-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="48e0b-109">podczas Rozmiar, w bajtach, obrazu w `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="48e0b-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="48e0b-110">podczas Bufor zawierający reprezentację binarną obrazu.</span><span class="sxs-lookup"><span data-stu-id="48e0b-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="48e0b-111">[in. out] Żądany maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="48e0b-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="48e0b-112">Po powrocie, rzeczywisty rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="48e0b-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48e0b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="48e0b-113">Return Value</span></span>  
 <span data-ttu-id="48e0b-114">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="48e0b-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48e0b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48e0b-115">Remarks</span></span>  
 <span data-ttu-id="48e0b-116">Jeśli funkcja `StrongNameGetBlobFromImage` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="48e0b-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e0b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48e0b-117">Requirements</span></span>  
 <span data-ttu-id="48e0b-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e0b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e0b-119">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="48e0b-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="48e0b-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="48e0b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48e0b-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e0b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e0b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48e0b-122">See also</span></span>

- [<span data-ttu-id="48e0b-123">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="48e0b-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="48e0b-124">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="48e0b-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="48e0b-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="48e0b-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
