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
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762100"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="ccfd0-102">ICLRStrongName::GetHashFromFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="ccfd0-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="ccfd0-103">Generuje skrót do zawartości pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccfd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccfd0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ccfd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccfd0-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ccfd0-106">podczas Nazwa Unicode pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ccfd0-107">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="ccfd0-108">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="ccfd0-109">Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ccfd0-110">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ccfd0-111">podczas Maksymalny rozmiar buforu wskazywany przez `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="ccfd0-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ccfd0-112">określoną Rozmiar, w bajtach, z `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="ccfd0-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccfd0-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ccfd0-113">Return Value</span></span>  
 <span data-ttu-id="ccfd0-114">`S_OK`Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="ccfd0-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccfd0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ccfd0-115">Remarks</span></span>  
 <span data-ttu-id="ccfd0-116">Ta metoda jest taka sama jak Metoda [ICLRStrongName:: GetHashFromFile —](iclrstrongname-gethashfromfile-method.md) , z tą różnicą, że Specyfikacja nazwy pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="ccfd0-116">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccfd0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ccfd0-117">Requirements</span></span>  
 <span data-ttu-id="ccfd0-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccfd0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccfd0-119">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="ccfd0-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ccfd0-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ccfd0-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccfd0-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccfd0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfd0-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ccfd0-122">See also</span></span>

- [<span data-ttu-id="ccfd0-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="ccfd0-123">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="ccfd0-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ccfd0-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
