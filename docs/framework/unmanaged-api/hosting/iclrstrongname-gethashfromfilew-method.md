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
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176373"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="7cc08-102">ICLRStrongName::GetHashFromFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="7cc08-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="7cc08-103">Generuje skrót nad zawartością pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="7cc08-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cc08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cc08-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7cc08-106">[w] Nazwa unicode pliku do mieszania.</span><span class="sxs-lookup"><span data-stu-id="7cc08-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="7cc08-107">[w, na zewnątrz] Algorytm do użycia podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="7cc08-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="7cc08-108">Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="7cc08-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="7cc08-109">Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="7cc08-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="7cc08-110">[na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="7cc08-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="7cc08-111">[w] Maksymalny rozmiar buforu wskazywowany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="7cc08-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="7cc08-112">[na zewnątrz] Rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="7cc08-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7cc08-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7cc08-113">Return Value</span></span>  
 <span data-ttu-id="7cc08-114">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7cc08-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cc08-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cc08-115">Remarks</span></span>  
 <span data-ttu-id="7cc08-116">Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody, z tą różnicą, że specyfikacja nazwy pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="7cc08-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cc08-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cc08-117">Requirements</span></span>  
 <span data-ttu-id="7cc08-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cc08-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cc08-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7cc08-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7cc08-120">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cc08-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cc08-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cc08-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc08-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cc08-122">See also</span></span>

- [<span data-ttu-id="7cc08-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="7cc08-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="7cc08-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7cc08-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
