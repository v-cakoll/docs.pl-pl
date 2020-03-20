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
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178072"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="634cc-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="634cc-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="634cc-103">Generuje skrót nad zawartością określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="634cc-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="634cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="634cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="634cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="634cc-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="634cc-106">[w] Nazwa pliku do mieszania.</span><span class="sxs-lookup"><span data-stu-id="634cc-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="634cc-107">[w, na zewnątrz] Algorytm do użycia podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="634cc-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="634cc-108">Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="634cc-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="634cc-109">Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="634cc-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="634cc-110">[na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="634cc-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="634cc-111">[w] Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="634cc-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="634cc-112">[na zewnątrz] Rozmiar (w bajtach) `pbHash`zwracanego .</span><span class="sxs-lookup"><span data-stu-id="634cc-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="634cc-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="634cc-113">Return Value</span></span>  
 <span data-ttu-id="634cc-114">`S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="634cc-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="634cc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="634cc-115">Remarks</span></span>  
 <span data-ttu-id="634cc-116">Ta metoda jest taka sama jak [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody, z tą różnicą, że specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="634cc-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="634cc-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="634cc-117">Requirements</span></span>  
 <span data-ttu-id="634cc-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="634cc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="634cc-119">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="634cc-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="634cc-120">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="634cc-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="634cc-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="634cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634cc-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="634cc-122">See also</span></span>

- [<span data-ttu-id="634cc-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="634cc-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="634cc-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="634cc-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
