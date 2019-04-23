---
title: GetHashFromAssemblyFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56a509d08b19cf449177984e7b59481eb7b09a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092165"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="567a5-102">GetHashFromAssemblyFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="567a5-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="567a5-103">Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="567a5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="567a5-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="567a5-104">This function has been deprecated.</span></span> <span data-ttu-id="567a5-105">Użyj [iclrstrongname::gethashfromassemblyfile —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="567a5-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="567a5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="567a5-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="567a5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="567a5-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="567a5-108">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="567a5-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="567a5-109">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="567a5-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="567a5-110">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="567a5-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="567a5-111">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="567a5-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="567a5-112">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="567a5-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="567a5-113">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="567a5-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="567a5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="567a5-114">Requirements</span></span>  
 <span data-ttu-id="567a5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="567a5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="567a5-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="567a5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="567a5-117">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="567a5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="567a5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="567a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="567a5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="567a5-119">See also</span></span>

- [<span data-ttu-id="567a5-120">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="567a5-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="567a5-121">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="567a5-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="567a5-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="567a5-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
