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
ms.openlocfilehash: 9561d383e7c134230b8664329b59aec23e487124
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899582"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="e2e93-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="e2e93-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="e2e93-103">Generuje skrót do zawartości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="e2e93-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2e93-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2e93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2e93-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e2e93-106">podczas Nazwa pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="e2e93-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e2e93-107">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="e2e93-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e2e93-108">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="e2e93-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e2e93-109">Jeśli wartość `piHashAlg` jest równa 0, używany jest algorytm domyślny CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="e2e93-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e2e93-110">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="e2e93-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e2e93-111">podczas Maksymalny rozmiar buforu, do którego `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="e2e93-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e2e93-112">określoną Rozmiar w bajtach zwracanej `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e2e93-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2e93-113">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="e2e93-113">Return Value</span></span>  
 <span data-ttu-id="e2e93-114">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="e2e93-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2e93-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2e93-115">Remarks</span></span>  
 <span data-ttu-id="e2e93-116">Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFileW —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2e93-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e93-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2e93-117">Requirements</span></span>  
 <span data-ttu-id="e2e93-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2e93-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e93-119">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="e2e93-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e2e93-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e2e93-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2e93-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e93-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e93-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2e93-122">See also</span></span>

- [<span data-ttu-id="e2e93-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="e2e93-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="e2e93-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e2e93-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
