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
ms.openlocfilehash: 7121ace6777e7cf947fcc6ff30b1ea314851feff
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636716"
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="53474-102">StrongNameKeyInstall — Funkcja</span><span class="sxs-lookup"><span data-stu-id="53474-102">StrongNameKeyInstall Function</span></span>

<span data-ttu-id="53474-103">Importuje pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="53474-103">Imports a public/private key pair into a container.</span></span>

<span data-ttu-id="53474-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="53474-104">This function has been deprecated.</span></span> <span data-ttu-id="53474-105">Użyj [iclrstrongname::strongnamekeyinstall —](../hosting/iclrstrongname-strongnamekeyinstall-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="53474-105">Use the [ICLRStrongName::StrongNameKeyInstall](../hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="53474-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="53474-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyInstall (
    [in]  LPCWSTR   wszKeyContainer,
    [in]  BYTE      *pbKeyBlob,
    [in]  ULONG     cbKeyBlob
);
```

## <a name="parameters"></a><span data-ttu-id="53474-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="53474-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="53474-108">[in] Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="53474-108">[in] The name of the key container.</span></span> <span data-ttu-id="53474-109">`wszKeyContainer` musi być ciągiem niepustym.</span><span class="sxs-lookup"><span data-stu-id="53474-109">`wszKeyContainer` must be a non-empty string.</span></span>

`pbKeyBlob`\
<span data-ttu-id="53474-110">[in] Binarny pary kluczy.</span><span class="sxs-lookup"><span data-stu-id="53474-110">[in] The binary key pair.</span></span>

`cbKeyBlob`\
<span data-ttu-id="53474-111">[in] Rozmiar w bajtach z `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="53474-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>

## <a name="return-value"></a><span data-ttu-id="53474-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53474-112">Return Value</span></span>

<span data-ttu-id="53474-113">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="53474-113">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="53474-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53474-114">Remarks</span></span>

<span data-ttu-id="53474-115">Użyj [StrongNameKeyDelete](strongnamekeydelete-function.md) funkcję, aby usunąć kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="53474-115">Use the [StrongNameKeyDelete](strongnamekeydelete-function.md) function to delete the key container.</span></span>

<span data-ttu-id="53474-116">Jeśli `StrongNameKeyInstall` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="53474-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="53474-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53474-117">Requirements</span></span>

<span data-ttu-id="53474-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53474-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="53474-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="53474-119">**Header:** StrongName.h</span></span>

<span data-ttu-id="53474-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="53474-120">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="53474-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53474-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="53474-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53474-122">See also</span></span>

- [<span data-ttu-id="53474-123">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="53474-123">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="53474-124">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="53474-124">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="53474-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="53474-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
