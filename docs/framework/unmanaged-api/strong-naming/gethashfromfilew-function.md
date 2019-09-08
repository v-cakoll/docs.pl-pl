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
ms.openlocfilehash: fd96b5acb22f63b6e06c981119186680d6593a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799186"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="aadf0-102">GetHashFromFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="aadf0-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="aadf0-103">Generuje skrót do zawartości pliku określonego przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="aadf0-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="aadf0-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aadf0-104">This function has been deprecated.</span></span> <span data-ttu-id="aadf0-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromFileW —](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="aadf0-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aadf0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="aadf0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="aadf0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aadf0-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="aadf0-108">podczas Nazwa Unicode pliku do skrótu.</span><span class="sxs-lookup"><span data-stu-id="aadf0-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="aadf0-109">[in. out] Algorytm, który ma być używany podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="aadf0-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="aadf0-110">Prawidłowymi algorytmami są te zdefiniowane przez interfejs CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="aadf0-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="aadf0-111">Jeśli `piHashAlg` jest ustawiona na 0, zostanie użyty domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="aadf0-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="aadf0-112">określoną Tablica bajtowa zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="aadf0-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="aadf0-113">podczas Maksymalny rozmiar buforu wskazywany przez `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="aadf0-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="aadf0-114">określoną Rozmiar, w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="aadf0-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aadf0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aadf0-115">Remarks</span></span>  
 <span data-ttu-id="aadf0-116">Ta funkcja jest taka sama jak [GetHashFromFile —](gethashfromfile-function.md), z tą różnicą, że Specyfikacja nazw plików jest Unicode zamiast ANSI.</span><span class="sxs-lookup"><span data-stu-id="aadf0-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aadf0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aadf0-117">Requirements</span></span>  
 <span data-ttu-id="aadf0-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aadf0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aadf0-119">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="aadf0-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="aadf0-120">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aadf0-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aadf0-121">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aadf0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadf0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aadf0-122">See also</span></span>

- [<span data-ttu-id="aadf0-123">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="aadf0-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="aadf0-124">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="aadf0-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="aadf0-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="aadf0-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
