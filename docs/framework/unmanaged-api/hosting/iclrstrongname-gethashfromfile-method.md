---
title: "ICLRStrongName::GetHashFromFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 480113148e039ff1be3e438b4af2e24fdeacba14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="d4d3c-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4d3c-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="d4d3c-103">Generuje skrót za pośrednictwem zawartość określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d3c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4d3c-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4d3c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4d3c-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="d4d3c-106">[in] Nazwa pliku do wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d4d3c-107">[w, out] Algorytm używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d4d3c-108">Prawidłowe algorytmy są zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d4d3c-109">Jeśli `piHashAlg` jest ustawiona na 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d4d3c-110">[out] Tablica bajtów zawierająca wygenerowanego wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d4d3c-111">[in] Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d4d3c-112">[out] Rozmiar w bajtach, zwracana `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4d3c-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d4d3c-113">Return Value</span></span>  
 <span data-ttu-id="d4d3c-114">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="d4d3c-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d3c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4d3c-115">Remarks</span></span>  
 <span data-ttu-id="d4d3c-116">Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metoda, z wyjątkiem tego, że nazwa pliku specyfikacji jest ANSI znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="d4d3c-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d3c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4d3c-117">Requirements</span></span>  
 <span data-ttu-id="d4d3c-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d3c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d3c-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d4d3c-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d4d3c-120">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4d3c-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4d3c-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d3c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d3c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4d3c-122">See Also</span></span>  
 [<span data-ttu-id="d4d3c-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="d4d3c-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="d4d3c-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="d4d3c-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
