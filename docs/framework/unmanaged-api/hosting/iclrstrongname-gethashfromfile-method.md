---
title: ICLRStrongName::GetHashFromFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1407bbcbb5bfa351a38f7627f2a89106c7d5136f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537663"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="32bc8-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="32bc8-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="32bc8-103">Generuje skrót nad zawartość określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="32bc8-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32bc8-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32bc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32bc8-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="32bc8-106">[in] Nazwa pliku do wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="32bc8-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="32bc8-107">[out w] Algorytm, który ma być używana podczas generowania skrótów.</span><span class="sxs-lookup"><span data-stu-id="32bc8-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="32bc8-108">Nieprawidłowa algorytmy są identyczne ze zdefiniowanymi przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="32bc8-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="32bc8-109">Jeśli `piHashAlg` jest równa 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="32bc8-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="32bc8-110">[out] Tablica bajtów zawierająca wygenerowanego skrótu.</span><span class="sxs-lookup"><span data-stu-id="32bc8-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="32bc8-111">[in] Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="32bc8-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="32bc8-112">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="32bc8-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32bc8-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32bc8-113">Return Value</span></span>  
 <span data-ttu-id="32bc8-114">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="32bc8-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32bc8-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32bc8-115">Remarks</span></span>  
 <span data-ttu-id="32bc8-116">Ta metoda jest taka sama jak [iclrstrongname::gethashfromfilew —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody, z tą różnicą, że specyfikacji nazwa pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="32bc8-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bc8-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32bc8-117">Requirements</span></span>  
 <span data-ttu-id="32bc8-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32bc8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bc8-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="32bc8-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="32bc8-120">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32bc8-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32bc8-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bc8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bc8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32bc8-122">See also</span></span>
- [<span data-ttu-id="32bc8-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="32bc8-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="32bc8-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="32bc8-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
