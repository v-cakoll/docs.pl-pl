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
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140729"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="2b5ca-102">GetHashFromAssemblyFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="2b5ca-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="2b5ca-103">Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2b5ca-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-104">This function has been deprecated.</span></span> <span data-ttu-id="2b5ca-105">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromAssemblyFile —](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2b5ca-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5ca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b5ca-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b5ca-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b5ca-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="2b5ca-108">podczas Ścieżka do pliku, który ma zostać poddany skrótowi.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2b5ca-109">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2b5ca-110">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2b5ca-111">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2b5ca-112">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2b5ca-113">określoną Zwrócony rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2b5ca-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b5ca-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b5ca-114">Requirements</span></span>  
 <span data-ttu-id="2b5ca-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b5ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b5ca-116">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="2b5ca-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2b5ca-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b5ca-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b5ca-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b5ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5ca-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b5ca-119">See also</span></span>

- [<span data-ttu-id="2b5ca-120">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="2b5ca-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="2b5ca-121">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="2b5ca-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="2b5ca-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b5ca-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
