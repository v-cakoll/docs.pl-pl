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
ms.openlocfilehash: 9db583c7064cb910b29e84437f31143dac0d3ec9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175086"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="f2c5f-102">GetHashFromFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="f2c5f-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="f2c5f-103">Generuje skrót nad zawartością pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="f2c5f-104">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-104">This function has been deprecated.</span></span> <span data-ttu-id="f2c5f-105">Zamiast tego należy użyć metody [ICLRStrongName::GetHashFromFileW.](../hosting/iclrstrongname-gethashfromfilew-method.md)</span><span class="sxs-lookup"><span data-stu-id="f2c5f-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c5f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2c5f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="f2c5f-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2c5f-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f2c5f-108">[w] Nazwa unicode pliku do mieszania.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f2c5f-109">[w, na zewnątrz] Algorytm do użycia podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="f2c5f-110">Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="f2c5f-111">Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f2c5f-112">[na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f2c5f-113">[w] Maksymalny rozmiar buforu wskazywowany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f2c5f-114">[na zewnątrz] Rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2c5f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2c5f-115">Remarks</span></span>  
 <span data-ttu-id="f2c5f-116">Ta funkcja jest taka sama jak [GetHashFromFile](gethashfromfile-function.md), z tą różnicą, że specyfikacja nazwy pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="f2c5f-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2c5f-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2c5f-117">Requirements</span></span>  
 <span data-ttu-id="f2c5f-118">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2c5f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2c5f-119">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="f2c5f-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f2c5f-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2c5f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2c5f-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2c5f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c5f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2c5f-122">See also</span></span>

- [<span data-ttu-id="f2c5f-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="f2c5f-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="f2c5f-124">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="f2c5f-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="f2c5f-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2c5f-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
