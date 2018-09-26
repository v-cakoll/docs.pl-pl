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
ms.openlocfilehash: a8d9e7d593c2a8a9cce798724b2705dee21a740e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075164"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="66281-102">ICLRStrongName::GetHashFromAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="66281-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="66281-103">Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="66281-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66281-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66281-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66281-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66281-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="66281-106">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="66281-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="66281-107">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="66281-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="66281-108">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="66281-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="66281-109">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="66281-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="66281-110">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="66281-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="66281-111">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="66281-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66281-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66281-112">Return Value</span></span>  
 <span data-ttu-id="66281-113">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="66281-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66281-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66281-114">Requirements</span></span>  
 <span data-ttu-id="66281-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66281-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66281-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="66281-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="66281-117">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66281-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66281-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66281-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66281-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66281-119">See Also</span></span>  
 [<span data-ttu-id="66281-120">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="66281-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="66281-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="66281-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
