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
ms.openlocfilehash: 20c5f6bbb58b85f42ec00e356eccc5fb41ce813c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036236"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="656c9-102">ICLRStrongName::GetHashFromHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="656c9-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="656c9-103">Generuje skrót nad zawartość pliku, który ma określone dojście do pliku, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="656c9-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="656c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="656c9-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="656c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="656c9-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="656c9-106">[in] Uchwyt pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="656c9-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="656c9-107">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="656c9-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="656c9-108">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="656c9-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="656c9-109">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="656c9-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="656c9-110">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="656c9-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="656c9-111">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="656c9-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="656c9-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="656c9-112">Return Value</span></span>  
 <span data-ttu-id="656c9-113">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="656c9-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656c9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="656c9-114">Requirements</span></span>  
 <span data-ttu-id="656c9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="656c9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656c9-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="656c9-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="656c9-117">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="656c9-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="656c9-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656c9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656c9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="656c9-119">See Also</span></span>  
 [<span data-ttu-id="656c9-120">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="656c9-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
