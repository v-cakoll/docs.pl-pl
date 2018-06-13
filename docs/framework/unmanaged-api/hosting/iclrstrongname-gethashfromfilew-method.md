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
ms.openlocfilehash: 87600781c90fe5e6e049af74a68859955153f3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433344"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="320e6-102">ICLRStrongName::GetHashFromFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="320e6-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="320e6-103">Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="320e6-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="320e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="320e6-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="320e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="320e6-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="320e6-106">[in] Nazwa pliku do wyznaczania wartości skrótu Unicode.</span><span class="sxs-lookup"><span data-stu-id="320e6-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="320e6-107">[w, out] Algorytm używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="320e6-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="320e6-108">Prawidłowe algorytmy są zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="320e6-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="320e6-109">Jeśli `piHashAlg` jest ustawiona na 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="320e6-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="320e6-110">[out] Tablica bajtów zawierająca wygenerowanego wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="320e6-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="320e6-111">[in] Maksymalny rozmiar buforu wskazywana przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="320e6-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="320e6-112">[out] Rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="320e6-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="320e6-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="320e6-113">Return Value</span></span>  
 <span data-ttu-id="320e6-114">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="320e6-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="320e6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="320e6-115">Remarks</span></span>  
 <span data-ttu-id="320e6-116">Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metoda, z wyjątkiem tego, że nazwa pliku specyfikacji jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="320e6-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="320e6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="320e6-117">Requirements</span></span>  
 <span data-ttu-id="320e6-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="320e6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="320e6-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="320e6-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="320e6-120">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="320e6-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="320e6-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="320e6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320e6-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="320e6-122">See Also</span></span>  
 [<span data-ttu-id="320e6-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="320e6-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="320e6-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="320e6-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
