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
ms.openlocfilehash: 9f984d44d0a8acb85562a58653dfd2882053a0ce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799286"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="4af98-102">GetHashFromAssemblyFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4af98-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="4af98-103">Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="4af98-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="4af98-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="4af98-104">This function has been deprecated.</span></span> <span data-ttu-id="4af98-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromAssemblyFile —](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4af98-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af98-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4af98-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4af98-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4af98-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="4af98-108">podczas Ścieżka do pliku, który ma zostać poddany skrótowi.</span><span class="sxs-lookup"><span data-stu-id="4af98-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4af98-109">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="4af98-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4af98-110">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="4af98-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4af98-111">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="4af98-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4af98-112">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4af98-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4af98-113">określoną Zwrócony rozmiar, w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4af98-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af98-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4af98-114">Requirements</span></span>  
 <span data-ttu-id="4af98-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4af98-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af98-116">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4af98-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4af98-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4af98-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4af98-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af98-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af98-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4af98-119">See also</span></span>

- [<span data-ttu-id="4af98-120">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="4af98-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="4af98-121">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="4af98-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="4af98-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="4af98-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
