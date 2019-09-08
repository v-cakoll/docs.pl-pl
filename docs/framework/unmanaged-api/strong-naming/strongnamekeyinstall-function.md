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
ms.openlocfilehash: 353898b72f41acd0c49a43ff05e54f61b99444c4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798993"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="cd94f-102">StrongNameKeyInstall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="cd94f-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="cd94f-103">Importuje parę kluczy publiczny/prywatny do kontenera.</span><span class="sxs-lookup"><span data-stu-id="cd94f-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="cd94f-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="cd94f-104">This function has been deprecated.</span></span> <span data-ttu-id="cd94f-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyInstall —](../hosting/iclrstrongname-strongnamekeyinstall-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cd94f-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd94f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd94f-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="cd94f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd94f-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="cd94f-108">podczas Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="cd94f-108">[in] The name of the key container.</span></span> <span data-ttu-id="cd94f-109">`wszKeyContainer`nie może być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="cd94f-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="cd94f-110">podczas Para kluczy binarnych.</span><span class="sxs-lookup"><span data-stu-id="cd94f-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="cd94f-111">podczas Rozmiar, w bajtach, z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cd94f-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd94f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cd94f-112">Return Value</span></span>

<span data-ttu-id="cd94f-113">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="cd94f-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd94f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd94f-114">Remarks</span></span>

<span data-ttu-id="cd94f-115">Aby usunąć kontener kluczy, użyj funkcji [StrongNameKeyDelete —](strongnamekeydelete-function.md) .</span><span class="sxs-lookup"><span data-stu-id="cd94f-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="cd94f-116">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameKeyInstall`</span><span class="sxs-lookup"><span data-stu-id="cd94f-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd94f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd94f-117">Requirements</span></span>

<span data-ttu-id="cd94f-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd94f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="cd94f-119">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cd94f-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="cd94f-120">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd94f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="cd94f-121">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd94f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cd94f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd94f-122">See also</span></span>

- [<span data-ttu-id="cd94f-123">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="cd94f-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="cd94f-124">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="cd94f-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="cd94f-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd94f-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
