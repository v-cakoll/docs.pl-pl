---
title: ICLRStrongName::GetHashFromFileW — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acfa5c138faa47c96600530ab923de102b173ed6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803460"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="35a95-102">ICLRStrongName::GetHashFromFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="35a95-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="35a95-103">Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="35a95-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a95-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35a95-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="35a95-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35a95-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="35a95-106">[in] Nazwa pliku do wyznaczania wartości skrótu Unicode.</span><span class="sxs-lookup"><span data-stu-id="35a95-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="35a95-107">[out w] Algorytm, który ma być używana podczas generowania skrótów.</span><span class="sxs-lookup"><span data-stu-id="35a95-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="35a95-108">Nieprawidłowa algorytmy są identyczne ze zdefiniowanymi przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="35a95-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="35a95-109">Jeśli `piHashAlg` jest równa 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="35a95-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="35a95-110">[out] Tablica bajtów zawierająca wygenerowanego skrótu.</span><span class="sxs-lookup"><span data-stu-id="35a95-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="35a95-111">[in] Maksymalny rozmiar buforu wskazywany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="35a95-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="35a95-112">[out] Rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="35a95-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35a95-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="35a95-113">Return Value</span></span>  
 <span data-ttu-id="35a95-114">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="35a95-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a95-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35a95-115">Remarks</span></span>  
 <span data-ttu-id="35a95-116">Ta metoda jest taka sama jak [iclrstrongname::gethashfromfile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, z tą różnicą, że specyfikacji nazwa pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="35a95-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a95-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35a95-117">Requirements</span></span>  
 <span data-ttu-id="35a95-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a95-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a95-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="35a95-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="35a95-120">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35a95-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35a95-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a95-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a95-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35a95-122">See Also</span></span>  
 [<span data-ttu-id="35a95-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="35a95-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="35a95-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="35a95-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
