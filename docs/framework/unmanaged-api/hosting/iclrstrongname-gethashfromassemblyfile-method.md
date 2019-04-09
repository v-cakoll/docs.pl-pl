---
title: ICLRStrongName::GetHashFromAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 714827da24b3fc0a334210fd94e61f80cb2afe49
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135765"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="203a1-102">ICLRStrongName::GetHashFromAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="203a1-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="203a1-103">Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="203a1-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="203a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="203a1-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="203a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="203a1-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="203a1-106">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="203a1-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="203a1-107">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="203a1-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="203a1-108">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="203a1-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="203a1-109">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="203a1-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="203a1-110">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="203a1-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="203a1-111">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="203a1-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="203a1-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="203a1-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="203a1-113">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="203a1-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="203a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="203a1-114">Requirements</span></span>  
 <span data-ttu-id="203a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="203a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="203a1-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="203a1-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="203a1-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="203a1-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="203a1-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="203a1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="203a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="203a1-119">See also</span></span>

- [<span data-ttu-id="203a1-120">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="203a1-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="203a1-121">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="203a1-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
