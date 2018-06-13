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
ms.openlocfilehash: 427d93a9aff527d36720c4199782fa104a66f8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455036"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="fe3fa-102">GetHashFromBlob — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fe3fa-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="fe3fa-103">Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="fe3fa-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-104">This function has been deprecated.</span></span> <span data-ttu-id="fe3fa-105">Użyj [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3fa-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe3fa-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fe3fa-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe3fa-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="fe3fa-108">[in] Wskaźnik do adresu blok pamięci, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="fe3fa-109">[in] Długość, w bajtach bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fe3fa-110">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="fe3fa-111">Użyj wartości zero dla domyślnego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fe3fa-112">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fe3fa-113">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fe3fa-114">[out] Rozmiar w bajtach, zwracana `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fe3fa-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3fa-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe3fa-115">Requirements</span></span>  
 <span data-ttu-id="fe3fa-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe3fa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3fa-117">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="fe3fa-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fe3fa-118">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe3fa-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe3fa-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3fa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3fa-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe3fa-120">See Also</span></span>  
 [<span data-ttu-id="fe3fa-121">GetHashFromBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="fe3fa-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="fe3fa-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="fe3fa-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
