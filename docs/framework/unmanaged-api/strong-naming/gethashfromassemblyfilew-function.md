---
title: GetHashFromAssemblyFileW — Funkcja
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140698"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="ce4f8-102">GetHashFromAssemblyFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ce4f8-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="ce4f8-103">Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="ce4f8-104">Ścieżka do pliku zestawu musi być określona jako ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="ce4f8-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-105">This function has been deprecated.</span></span> <span data-ttu-id="ce4f8-106">Zamiast tego użyj metody [ICLRStrongName:: GetHashFromAssemblyFileW —](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ce4f8-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4f8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce4f8-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce4f8-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce4f8-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ce4f8-109">podczas Ścieżka do pliku, który ma zostać poddany skrótowi.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="ce4f8-110">Ten parametr musi być ciągiem Unicode.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ce4f8-111">[in. out] Stała, która określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ce4f8-112">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ce4f8-113">określoną Zwrócony bufor wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ce4f8-114">podczas Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ce4f8-115">określoną Zwrócony rozmiar w bajtach `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ce4f8-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce4f8-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce4f8-116">Requirements</span></span>  
 <span data-ttu-id="ce4f8-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce4f8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce4f8-118">**Nagłówek:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ce4f8-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ce4f8-119">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce4f8-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce4f8-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce4f8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4f8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce4f8-121">See also</span></span>

- [<span data-ttu-id="ce4f8-122">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="ce4f8-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="ce4f8-123">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="ce4f8-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="ce4f8-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce4f8-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
