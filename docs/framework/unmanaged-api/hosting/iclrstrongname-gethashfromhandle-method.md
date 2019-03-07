---
title: ICLRStrongName::GetHashFromHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9688635532e0ccc35ff8826a53da80738bfc528e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470023"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="455a1-102">ICLRStrongName::GetHashFromHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="455a1-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="455a1-103">Generuje skrót nad zawartość pliku, który ma określone dojście do pliku, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="455a1-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="455a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="455a1-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="455a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="455a1-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="455a1-106">[in] Uchwyt pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="455a1-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="455a1-107">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="455a1-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="455a1-108">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="455a1-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="455a1-109">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="455a1-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="455a1-110">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="455a1-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="455a1-111">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="455a1-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="455a1-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="455a1-112">Return Value</span></span>  
 <span data-ttu-id="455a1-113">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="455a1-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="455a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="455a1-114">Requirements</span></span>  
 <span data-ttu-id="455a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="455a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="455a1-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="455a1-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="455a1-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="455a1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="455a1-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="455a1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="455a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="455a1-119">See also</span></span>
- [<span data-ttu-id="455a1-120">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="455a1-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
