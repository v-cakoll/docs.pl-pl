---
title: GetHashFromFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d27db0d49e7e1c8c1becaf5bc32b22adf480e573
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478572"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="032e7-102">GetHashFromFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="032e7-102">GetHashFromFile Function</span></span>
<span data-ttu-id="032e7-103">Generuje skrót nad zawartość określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="032e7-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="032e7-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="032e7-104">This function has been deprecated.</span></span> <span data-ttu-id="032e7-105">Użyj [iclrstrongname::gethashfromfile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="032e7-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="032e7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="032e7-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="032e7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="032e7-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="032e7-108">[in] Nazwa pliku do wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="032e7-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="032e7-109">[out w] Algorytm, który ma być używana podczas generowania skrótów.</span><span class="sxs-lookup"><span data-stu-id="032e7-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="032e7-110">Nieprawidłowa algorytmy są identyczne ze zdefiniowanymi przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="032e7-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="032e7-111">Jeśli `piHashAlg` jest równa 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="032e7-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="032e7-112">[out] Tablica bajtów zawierająca wygenerowanego skrótu.</span><span class="sxs-lookup"><span data-stu-id="032e7-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="032e7-113">[in] Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="032e7-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="032e7-114">[out] Rozmiar w bajtach zwracanego `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="032e7-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="032e7-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="032e7-115">Remarks</span></span>  
 <span data-ttu-id="032e7-116">Ta funkcja jest taka sama jak [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), chyba że specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="032e7-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="032e7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="032e7-117">Requirements</span></span>  
 <span data-ttu-id="032e7-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="032e7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032e7-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="032e7-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="032e7-120">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="032e7-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="032e7-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="032e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032e7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="032e7-122">See also</span></span>
- [<span data-ttu-id="032e7-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="032e7-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="032e7-124">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="032e7-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="032e7-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="032e7-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
