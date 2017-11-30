---
title: "GetHashFromFileW — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFileW
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFileW
helpviewer_keywords: GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c19047f03279b1284ea8b5b8f99785cfaff5146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="0958a-102">GetHashFromFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0958a-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="0958a-103">Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="0958a-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="0958a-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="0958a-104">This function has been deprecated.</span></span> <span data-ttu-id="0958a-105">Użyj [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="0958a-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0958a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0958a-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="0958a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0958a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0958a-108">[in] Nazwa pliku do wyznaczania wartości skrótu Unicode.</span><span class="sxs-lookup"><span data-stu-id="0958a-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0958a-109">[w, out] Algorytm używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="0958a-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="0958a-110">Prawidłowe algorytmy są zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="0958a-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="0958a-111">Jeśli `piHashAlg` jest ustawiona na 0, CALG_SHA 1 jest używany domyślny algorytm.</span><span class="sxs-lookup"><span data-stu-id="0958a-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0958a-112">[out] Tablica bajtów zawierająca wygenerowanego wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="0958a-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0958a-113">[in] Maksymalny rozmiar buforu wskazywana przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0958a-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0958a-114">[out] Rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0958a-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0958a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0958a-115">Remarks</span></span>  
 <span data-ttu-id="0958a-116">Ta funkcja jest taka sama jak [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), ale specyfikacja nazwy pliku jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="0958a-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0958a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0958a-117">Requirements</span></span>  
 <span data-ttu-id="0958a-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0958a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0958a-119">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0958a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0958a-120">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0958a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0958a-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0958a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0958a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0958a-122">See Also</span></span>  
 [<span data-ttu-id="0958a-123">GetHashFromFileW — metoda</span><span class="sxs-lookup"><span data-stu-id="0958a-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="0958a-124">GetHashFromFile — metoda</span><span class="sxs-lookup"><span data-stu-id="0958a-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="0958a-125">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="0958a-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
