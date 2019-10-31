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
ms.openlocfilehash: 798bb0585bfe4cc29afba2fbefae818301704613
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135192"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="4e5c6-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e5c6-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="4e5c6-103">Generuje skrót do zawartości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e5c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e5c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e5c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e5c6-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="4e5c6-106">podczas Nazwa pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4e5c6-107">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="4e5c6-108">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="4e5c6-109">Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4e5c6-110">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4e5c6-111">podczas Maksymalny rozmiar buforu, do którego `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4e5c6-112">określoną Rozmiar w bajtach zwracanej `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e5c6-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e5c6-113">Return Value</span></span>  
 <span data-ttu-id="4e5c6-114">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="4e5c6-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e5c6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e5c6-115">Remarks</span></span>  
 <span data-ttu-id="4e5c6-116">Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFileW —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="4e5c6-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e5c6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e5c6-117">Requirements</span></span>  
 <span data-ttu-id="4e5c6-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e5c6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e5c6-119">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="4e5c6-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4e5c6-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e5c6-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e5c6-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e5c6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5c6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e5c6-122">See also</span></span>

- [<span data-ttu-id="4e5c6-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="4e5c6-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="4e5c6-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e5c6-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
