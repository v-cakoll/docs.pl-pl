---
title: GetHashFromFileW — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140676"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="fc8d2-102">GetHashFromFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="fc8d2-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="fc8d2-103">Generuje skrót do zawartości pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="fc8d2-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-104">This function has been deprecated.</span></span> <span data-ttu-id="fc8d2-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromFileW —](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc8d2-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8d2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc8d2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fc8d2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc8d2-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fc8d2-108">podczas Nazwa Unicode pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fc8d2-109">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="fc8d2-110">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="fc8d2-111">Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fc8d2-112">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fc8d2-113">podczas Maksymalny rozmiar buforu wskazywany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fc8d2-114">określoną Rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc8d2-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc8d2-115">Remarks</span></span>  
 <span data-ttu-id="fc8d2-116">Ta funkcja jest taka sama jak [GetHashFromFile —](gethashfromfile-function.md), z tą różnicą, że Specyfikacja nazw plików jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="fc8d2-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8d2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc8d2-117">Requirements</span></span>  
 <span data-ttu-id="fc8d2-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc8d2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8d2-119">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="fc8d2-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fc8d2-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc8d2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8d2-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8d2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8d2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc8d2-122">See also</span></span>

- [<span data-ttu-id="fc8d2-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="fc8d2-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="fc8d2-124">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="fc8d2-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="fc8d2-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc8d2-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
