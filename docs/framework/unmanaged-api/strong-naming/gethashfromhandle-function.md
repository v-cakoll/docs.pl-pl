---
title: GetHashFromHandle — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: defa18bde8e5ce0f1cc7ff040aaa4fa0e95fd7e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619229"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="c9c13-102">GetHashFromHandle — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c9c13-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="c9c13-103">Generuje skrót nad zawartość pliku przy użyciu określone dojście do pliku, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="c9c13-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="c9c13-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="c9c13-104">This function has been deprecated.</span></span> <span data-ttu-id="c9c13-105">Użyj [iclrstrongname::gethashfromhandle —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c9c13-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c13-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9c13-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9c13-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9c13-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="c9c13-108">[in] Uchwyt pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="c9c13-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c9c13-109">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c9c13-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c9c13-110">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="c9c13-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c9c13-111">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="c9c13-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c9c13-112">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c9c13-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c9c13-113">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c9c13-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9c13-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9c13-114">Requirements</span></span>  
 <span data-ttu-id="c9c13-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9c13-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9c13-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c9c13-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c9c13-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9c13-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9c13-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c13-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c13-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9c13-119">See also</span></span>
- [<span data-ttu-id="c9c13-120">GetHashFromHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="c9c13-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="c9c13-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9c13-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
