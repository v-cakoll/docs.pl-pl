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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a88adec508d80a40ec044e5011d3115e197e334
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137491"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="b71a3-102">GetHashFromAssemblyFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b71a3-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="b71a3-103">Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="b71a3-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="b71a3-104">Należy określić ścieżkę do pliku zestawu jako ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="b71a3-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="b71a3-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="b71a3-105">This function has been deprecated.</span></span> <span data-ttu-id="b71a3-106">Użyj [iclrstrongname::gethashfromassemblyfilew —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b71a3-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b71a3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b71a3-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b71a3-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="b71a3-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b71a3-109">[in] Ścieżka do pliku ma zostać obliczona wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="b71a3-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="b71a3-110">Ten parametr musi być ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="b71a3-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b71a3-111">[out w] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="b71a3-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="b71a3-112">Użyj wartości zero dla domyślnego algorytmu wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="b71a3-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b71a3-113">[out] Bufor zwrócone wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="b71a3-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b71a3-114">[in] Żądany maksymalny rozmiar `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b71a3-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b71a3-115">[out] Zwrócone rozmiar w bajtach, z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b71a3-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b71a3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b71a3-116">Requirements</span></span>  
 <span data-ttu-id="b71a3-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b71a3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b71a3-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b71a3-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b71a3-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b71a3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b71a3-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b71a3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b71a3-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b71a3-121">See also</span></span>

- [<span data-ttu-id="b71a3-122">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="b71a3-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="b71a3-123">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="b71a3-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="b71a3-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="b71a3-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
