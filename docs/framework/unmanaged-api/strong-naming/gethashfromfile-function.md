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
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176984"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="ac62d-102">GetHashFromFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ac62d-102">GetHashFromFile Function</span></span>
<span data-ttu-id="ac62d-103">Generuje skrót nad zawartością określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="ac62d-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="ac62d-104">Ta funkcja została przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ac62d-104">This function has been deprecated.</span></span> <span data-ttu-id="ac62d-105">Zamiast tego należy użyć metody [ICLRStrongName::GetHashFromFile.](../hosting/iclrstrongname-gethashfromfile-method.md)</span><span class="sxs-lookup"><span data-stu-id="ac62d-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac62d-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac62d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac62d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac62d-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="ac62d-108">[w] Nazwa pliku do mieszania.</span><span class="sxs-lookup"><span data-stu-id="ac62d-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ac62d-109">[w, na zewnątrz] Algorytm do użycia podczas generowania skrótu.</span><span class="sxs-lookup"><span data-stu-id="ac62d-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="ac62d-110">Prawidłowe algorytmy są zdefiniowane przez Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="ac62d-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="ac62d-111">Jeśli `piHashAlg` jest ustawiona na 0, używany jest domyślny algorytm CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="ac62d-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ac62d-112">[na zewnątrz] Tablica bajtów zawierająca wygenerowany skrót.</span><span class="sxs-lookup"><span data-stu-id="ac62d-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ac62d-113">[w] Maksymalny rozmiar buforu, który `pbHash` wskazuje.</span><span class="sxs-lookup"><span data-stu-id="ac62d-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ac62d-114">[na zewnątrz] Rozmiar (w bajtach) `pbHash`zwracanego .</span><span class="sxs-lookup"><span data-stu-id="ac62d-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac62d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac62d-115">Remarks</span></span>  
 <span data-ttu-id="ac62d-116">Ta funkcja jest taka sama jak [GetHashFromFileW](gethashfromfilew-function.md), z tą różnicą, że specyfikacja nazwy pliku jest ANSI zamiast Unicode.</span><span class="sxs-lookup"><span data-stu-id="ac62d-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac62d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac62d-117">Requirements</span></span>  
 <span data-ttu-id="ac62d-118">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac62d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac62d-119">**Nagłówek:** StrongName.h (Nazwa siła)-h</span><span class="sxs-lookup"><span data-stu-id="ac62d-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ac62d-120">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac62d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac62d-121">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac62d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac62d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac62d-122">See also</span></span>

- [<span data-ttu-id="ac62d-123">GetHashFromFile, metoda</span><span class="sxs-lookup"><span data-stu-id="ac62d-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="ac62d-124">GetHashFromFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="ac62d-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="ac62d-125">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac62d-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
