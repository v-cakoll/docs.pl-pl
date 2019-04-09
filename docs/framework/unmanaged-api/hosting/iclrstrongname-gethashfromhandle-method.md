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
ms.openlocfilehash: 6d11c71498053844792cd902959dee642877c46b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146981"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="9b2f7-102">ICLRStrongName::GetHashFromHandle — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b2f7-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="9b2f7-103">Generuje skrót nad zawartość pliku, który ma określone dojście do pliku, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b2f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b2f7-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b2f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b2f7-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="9b2f7-106">[in] Uchwyt pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9b2f7-107">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9b2f7-108">Użyj wartości zero dla domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9b2f7-109">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9b2f7-110">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9b2f7-111">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9b2f7-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b2f7-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b2f7-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="9b2f7-113">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="9b2f7-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b2f7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b2f7-114">Requirements</span></span>  
 <span data-ttu-id="9b2f7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b2f7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b2f7-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9b2f7-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9b2f7-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b2f7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9b2f7-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9b2f7-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9b2f7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b2f7-119">See also</span></span>

- [<span data-ttu-id="9b2f7-120">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9b2f7-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
