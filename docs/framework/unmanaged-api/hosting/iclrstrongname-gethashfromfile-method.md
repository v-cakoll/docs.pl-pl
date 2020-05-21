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
ms.openlocfilehash: e4a5f6440a016176cf06704b342c173b29748e78
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762113"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="b2b7a-102">ICLRStrongName::GetHashFromFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2b7a-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="b2b7a-103">Generuje skrót do zawartości określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2b7a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2b7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2b7a-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="b2b7a-106">podczas Nazwa pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b2b7a-107">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b2b7a-108">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b2b7a-109">Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b2b7a-110">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b2b7a-111">podczas Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b2b7a-112">określoną Rozmiar zwracanych wartości (w bajtach) `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="b2b7a-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2b7a-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b2b7a-113">Return Value</span></span>  
 <span data-ttu-id="b2b7a-114">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="b2b7a-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2b7a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2b7a-115">Remarks</span></span>  
 <span data-ttu-id="b2b7a-116">Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFileW —](iclrstrongname-gethashfromfilew-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="b2b7a-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b7a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2b7a-117">Requirements</span></span>  
 <span data-ttu-id="b2b7a-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b7a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b7a-119">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="b2b7a-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b2b7a-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b2b7a-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b7a-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b7a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b7a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2b7a-122">See also</span></span>

- [<span data-ttu-id="b2b7a-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b7a-123">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="b2b7a-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2b7a-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
