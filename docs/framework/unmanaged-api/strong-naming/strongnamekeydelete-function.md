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
ms.openlocfilehash: d37f990241ae704abef55d863da0f40a31284837
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141585"
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="7799d-102">StrongNameKeyDelete — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7799d-102">StrongNameKeyDelete Function</span></span>

<span data-ttu-id="7799d-103">Usuwa określony kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="7799d-103">Deletes the specified key container.</span></span>

<span data-ttu-id="7799d-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7799d-104">This function has been deprecated.</span></span> <span data-ttu-id="7799d-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameKeyDelete —](../hosting/iclrstrongname-strongnamekeydelete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7799d-105">Use the [ICLRStrongName::StrongNameKeyDelete](../hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="7799d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7799d-106">Syntax</span></span>

```cpp
BOOLEAN StrongNameKeyDelete (
    [in]  LPCWSTR   wszKeyContainer
);
```

## <a name="parameters"></a><span data-ttu-id="7799d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7799d-107">Parameters</span></span>

`wszKeyContainer`\
<span data-ttu-id="7799d-108">podczas Nazwa kontenera kluczy do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="7799d-108">[in] The name of the key container to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="7799d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7799d-109">Return Value</span></span>

<span data-ttu-id="7799d-110">`true` po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7799d-110">`true` on successful completion; otherwise, `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7799d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7799d-111">Remarks</span></span>

<span data-ttu-id="7799d-112">Użyj funkcji [StrongNameKeyInstall —](strongnamekeyinstall-function.md) , aby zaimportować parę kluczy publicznych/prywatnych do kontenera.</span><span class="sxs-lookup"><span data-stu-id="7799d-112">Use the [StrongNameKeyInstall](strongnamekeyinstall-function.md) function to import a public/private key pair into a container.</span></span>

<span data-ttu-id="7799d-113">Jeśli funkcja `StrongNameKeyDelete` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.</span><span class="sxs-lookup"><span data-stu-id="7799d-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>

## <a name="requirements"></a><span data-ttu-id="7799d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7799d-114">Requirements</span></span>

<span data-ttu-id="7799d-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7799d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7799d-116">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="7799d-116">**Header:** StrongName.h</span></span>

<span data-ttu-id="7799d-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7799d-117">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="7799d-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7799d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7799d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7799d-119">See also</span></span>

- [<span data-ttu-id="7799d-120">StrongNameKeyDelete, metoda</span><span class="sxs-lookup"><span data-stu-id="7799d-120">StrongNameKeyDelete Method</span></span>](../hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="7799d-121">StrongNameKeyInstall, metoda</span><span class="sxs-lookup"><span data-stu-id="7799d-121">StrongNameKeyInstall Method</span></span>](../hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="7799d-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7799d-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
