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
ms.openlocfilehash: 30aad6fc62c8fee7448163ca69117b804203d505
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456485"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="7ba49-102">GetHashFromHandle — Funkcja</span><span class="sxs-lookup"><span data-stu-id="7ba49-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="7ba49-103">Generuje skrót za pośrednictwem zawartość pliku z dojściem określonego pliku, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="7ba49-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="7ba49-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7ba49-104">This function has been deprecated.</span></span> <span data-ttu-id="7ba49-105">Użyj [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="7ba49-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba49-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ba49-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ba49-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ba49-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="7ba49-108">[in] Dojście do pliku, który ma być mieszany.</span><span class="sxs-lookup"><span data-stu-id="7ba49-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="7ba49-109">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="7ba49-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="7ba49-110">Użyj wartości zero dla domyślnego algorytmu.</span><span class="sxs-lookup"><span data-stu-id="7ba49-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="7ba49-111">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="7ba49-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="7ba49-112">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="7ba49-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="7ba49-113">[out] Rozmiar w bajtach, zwracana `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="7ba49-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ba49-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ba49-114">Requirements</span></span>  
 <span data-ttu-id="7ba49-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ba49-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ba49-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="7ba49-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7ba49-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ba49-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7ba49-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ba49-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba49-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ba49-119">See Also</span></span>  
 [<span data-ttu-id="7ba49-120">GetHashFromHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="7ba49-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="7ba49-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ba49-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
