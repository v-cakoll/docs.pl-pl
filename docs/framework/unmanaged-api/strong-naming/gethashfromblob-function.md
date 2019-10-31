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
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140711"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="df6d1-102">GetHashFromBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="df6d1-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="df6d1-103">Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="df6d1-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="df6d1-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="df6d1-104">This function has been deprecated.</span></span> <span data-ttu-id="df6d1-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromBlob —](../hosting/iclrstrongname-gethashfromblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="df6d1-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="df6d1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="df6d1-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="df6d1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="df6d1-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="df6d1-108">podczas Wskaźnik do adresu bloku pamięci, który ma zostać zmieszany.</span><span class="sxs-lookup"><span data-stu-id="df6d1-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="df6d1-109">podczas Długość (w bajtach) bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="df6d1-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="df6d1-110">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="df6d1-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="df6d1-111">Użyj wartości zero dla algorytmu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="df6d1-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="df6d1-112">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="df6d1-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="df6d1-113">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="df6d1-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="df6d1-114">określoną Rozmiar w bajtach zwracanej `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="df6d1-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="df6d1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df6d1-115">Requirements</span></span>

<span data-ttu-id="df6d1-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df6d1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="df6d1-117">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="df6d1-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="df6d1-118">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="df6d1-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="df6d1-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df6d1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="df6d1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df6d1-120">See also</span></span>

- [<span data-ttu-id="df6d1-121">GetHashFromBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="df6d1-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="df6d1-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="df6d1-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
