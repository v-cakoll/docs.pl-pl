---
title: StrongNameKeyDelete — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 717d2104db8addf40e5187cee4cc8c46e5dc355e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636737"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="e8ff5-102">StrongNameKeyDelete — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e8ff5-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="e8ff5-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-103">Deletes the specified key container.</span></span>

<span data-ttu-id="e8ff5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-104">This function has been deprecated.</span></span> <span data-ttu-id="e8ff5-105">Użyj [iclrstrongname::strongnamekeydelete —](../hosting/iclrstrongname-strongnamekeydelete-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8ff5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ff5-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="e8ff5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8ff5-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="e8ff5-108">[in] Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8ff5-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8ff5-109">Return Value</span></span>

<span data-ttu-id="e8ff5-110">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8ff5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8ff5-111">Remarks</span></span>

<span data-ttu-id="e8ff5-112">Użyj [StrongNameKeyInstall](strongnamekeyinstall-function.md) funkcji do zaimportowania pary kluczy publiczny/prywatny w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="e8ff5-113">Jeśli `StrongNameKeyDelete` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e8ff5-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="e8ff5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ff5-114">Requirements</span></span>

<span data-ttu-id="e8ff5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ff5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e8ff5-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e8ff5-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="e8ff5-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8ff5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="e8ff5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ff5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e8ff5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8ff5-119">See also</span></span>

- [<span data-ttu-id="e8ff5-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="e8ff5-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="e8ff5-121">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="e8ff5-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="e8ff5-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8ff5-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
