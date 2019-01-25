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
ms.openlocfilehash: 6bfa846aa66345e23e085ca148c7e3f492c529f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576346"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="d183c-102">GetHashFromBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d183c-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="d183c-103">Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="d183c-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="d183c-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="d183c-104">This function has been deprecated.</span></span> <span data-ttu-id="d183c-105">Użyj [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="d183c-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d183c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d183c-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d183c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d183c-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="d183c-108">[in] Wskaźnik na adres bloku pamięci, aby zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="d183c-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="d183c-109">[in] Długość w bajtach, bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="d183c-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d183c-110">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d183c-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d183c-111">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="d183c-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d183c-112">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d183c-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d183c-113">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d183c-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d183c-114">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d183c-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d183c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d183c-115">Requirements</span></span>  
 <span data-ttu-id="d183c-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d183c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d183c-117">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d183c-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d183c-118">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d183c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d183c-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d183c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d183c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d183c-120">See also</span></span>
- [<span data-ttu-id="d183c-121">GetHashFromBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="d183c-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="d183c-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d183c-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
