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
ms.openlocfilehash: e5821abed4d6c7f7595bad3240ab86d5a128d794
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901147"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="c22cf-102">ICLRStrongName::GetHashFromFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="c22cf-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="c22cf-103">Generuje skrót do zawartości pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="c22cf-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c22cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c22cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c22cf-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c22cf-106">podczas Nazwa Unicode pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="c22cf-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c22cf-107">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="c22cf-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c22cf-108">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="c22cf-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c22cf-109">Jeśli wartość `piHashAlg` jest równa 0, używany jest algorytm domyślny CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="c22cf-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c22cf-110">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="c22cf-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c22cf-111">podczas Maksymalny rozmiar buforu wskazywany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c22cf-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c22cf-112">określoną Rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c22cf-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c22cf-113">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="c22cf-113">Return Value</span></span>  
 <span data-ttu-id="c22cf-114">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="c22cf-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c22cf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c22cf-115">Remarks</span></span>  
 <span data-ttu-id="c22cf-116">Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="c22cf-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c22cf-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c22cf-117">Requirements</span></span>  
 <span data-ttu-id="c22cf-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c22cf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c22cf-119">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="c22cf-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c22cf-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c22cf-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c22cf-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c22cf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c22cf-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c22cf-122">See also</span></span>

- [<span data-ttu-id="c22cf-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="c22cf-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="c22cf-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="c22cf-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
