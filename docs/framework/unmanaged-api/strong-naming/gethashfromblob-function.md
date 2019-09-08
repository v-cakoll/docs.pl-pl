---
title: GetHashFromBlob — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799230"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="14438-102">GetHashFromBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="14438-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="14438-103">Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="14438-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="14438-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="14438-104">This function has been deprecated.</span></span> <span data-ttu-id="14438-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromBlob —](../hosting/iclrstrongname-gethashfromblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14438-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="14438-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="14438-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="14438-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="14438-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="14438-108">podczas Wskaźnik do adresu bloku pamięci, który ma zostać zmieszany.</span><span class="sxs-lookup"><span data-stu-id="14438-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="14438-109">podczas Długość (w bajtach) bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="14438-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="14438-110">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="14438-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="14438-111">Użyj wartości zero dla algorytmu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="14438-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="14438-112">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="14438-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="14438-113">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="14438-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="14438-114">określoną Rozmiar zwracanych `pbHash`wartości (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="14438-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="14438-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14438-115">Requirements</span></span>

<span data-ttu-id="14438-116">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14438-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="14438-117">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="14438-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="14438-118">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="14438-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="14438-119">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14438-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="14438-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14438-120">See also</span></span>

- [<span data-ttu-id="14438-121">GetHashFromBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="14438-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="14438-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="14438-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
