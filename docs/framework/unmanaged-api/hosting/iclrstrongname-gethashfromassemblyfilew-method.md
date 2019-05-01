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
ms.openlocfilehash: 578dd7941ad7a2cf1d39a3aeed7fa823eb7efa79
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984597"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="70896-102">ICLRStrongName::GetHashFromAssemblyFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="70896-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="70896-103">Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="70896-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70896-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70896-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70896-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70896-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="70896-106">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="70896-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="70896-107">Ten parametr musi być ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="70896-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="70896-108">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="70896-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="70896-109">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="70896-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="70896-110">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="70896-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="70896-111">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="70896-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="70896-112">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="70896-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70896-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="70896-113">Return Value</span></span>  
 <span data-ttu-id="70896-114">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="70896-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70896-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70896-115">Requirements</span></span>  
 <span data-ttu-id="70896-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70896-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70896-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="70896-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="70896-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70896-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70896-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70896-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70896-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70896-120">See also</span></span>

- [<span data-ttu-id="70896-121">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="70896-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="70896-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="70896-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
