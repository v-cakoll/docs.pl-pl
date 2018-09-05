---
title: ICLRStrongName::GetHashFromAssemblyFileW — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7686a84759f8ac40a123d2c9a7b8f1b9b8096cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672603"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="29ce8-102">ICLRStrongName::GetHashFromAssemblyFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="29ce8-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="29ce8-103">Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="29ce8-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ce8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29ce8-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29ce8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29ce8-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="29ce8-106">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="29ce8-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="29ce8-107">Ten parametr musi być ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="29ce8-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="29ce8-108">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="29ce8-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="29ce8-109">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="29ce8-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="29ce8-110">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="29ce8-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="29ce8-111">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="29ce8-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="29ce8-112">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="29ce8-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29ce8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29ce8-113">Return Value</span></span>  
 <span data-ttu-id="29ce8-114">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="29ce8-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ce8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29ce8-115">Requirements</span></span>  
 <span data-ttu-id="29ce8-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ce8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ce8-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="29ce8-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="29ce8-118">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29ce8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29ce8-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ce8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ce8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29ce8-120">See Also</span></span>  
 [<span data-ttu-id="29ce8-121">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="29ce8-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="29ce8-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="29ce8-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
