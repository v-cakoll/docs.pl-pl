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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77b164cdec0dd224042e4de3265d14a4991d60ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771888"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="29b50-102">GetHashFromFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="29b50-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="29b50-103">Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="29b50-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="29b50-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="29b50-104">This function has been deprecated.</span></span> <span data-ttu-id="29b50-105">Użyj [iclrstrongname::gethashfromfilew —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="29b50-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b50-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="29b50-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="29b50-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="29b50-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="29b50-108">[in] Nazwa pliku do wyznaczania wartości skrótu Unicode.</span><span class="sxs-lookup"><span data-stu-id="29b50-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="29b50-109">[out w] Algorytm, który ma być używana podczas generowania skrótów.</span><span class="sxs-lookup"><span data-stu-id="29b50-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="29b50-110">Nieprawidłowa algorytmy są identyczne ze zdefiniowanymi przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="29b50-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="29b50-111">Jeśli `piHashAlg` jest równa 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="29b50-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="29b50-112">[out] Tablica bajtów zawierająca wygenerowanego skrótu.</span><span class="sxs-lookup"><span data-stu-id="29b50-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="29b50-113">[in] Maksymalny rozmiar buforu wskazywany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="29b50-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="29b50-114">[out] Rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="29b50-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29b50-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29b50-115">Remarks</span></span>  
 <span data-ttu-id="29b50-116">Ta funkcja jest taka sama jak [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), z tą różnicą, że specyfikacja nazwy plików Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="29b50-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b50-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29b50-117">Requirements</span></span>  
 <span data-ttu-id="29b50-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b50-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b50-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="29b50-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="29b50-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29b50-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29b50-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b50-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b50-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29b50-122">See also</span></span>

- [<span data-ttu-id="29b50-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="29b50-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="29b50-124">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="29b50-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="29b50-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="29b50-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
