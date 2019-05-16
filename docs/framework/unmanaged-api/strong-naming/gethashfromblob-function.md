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
ms.openlocfilehash: 6ba049723710b378a90d17c67735a05e8a09d05d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636850"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="b57f2-102">GetHashFromBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b57f2-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="b57f2-103">Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="b57f2-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="b57f2-104">This function has been deprecated.</span></span> <span data-ttu-id="b57f2-105">Użyj [iclrstrongname::gethashfromblob —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b57f2-105">Use the [ICLRStrongName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="b57f2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b57f2-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b57f2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="b57f2-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="b57f2-108">[in] Wskaźnik na adres bloku pamięci, aby zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="b57f2-109">[in] Długość w bajtach, bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="b57f2-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="b57f2-110">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b57f2-111">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="b57f2-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="b57f2-112">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="b57f2-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="b57f2-113">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b57f2-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="b57f2-114">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b57f2-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b57f2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b57f2-115">Requirements</span></span>

<span data-ttu-id="b57f2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b57f2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b57f2-117">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b57f2-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="b57f2-118">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b57f2-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="b57f2-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b57f2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b57f2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b57f2-120">See also</span></span>

- [<span data-ttu-id="b57f2-121">GetHashFromBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="b57f2-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="b57f2-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b57f2-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
