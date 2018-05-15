---
title: ICLRStrongName::GetHashFromAssemblyFileW — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36e4f07f04968579be2e42efad666b0453cc4796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="85eb5-102">ICLRStrongName::GetHashFromAssemblyFileW — Metoda</span><span class="sxs-lookup"><span data-stu-id="85eb5-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="85eb5-103">Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="85eb5-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85eb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85eb5-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85eb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85eb5-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="85eb5-106">[in] Ścieżka do pliku, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="85eb5-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="85eb5-107">Ten parametr musi być ciągiem Unicode.</span><span class="sxs-lookup"><span data-stu-id="85eb5-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="85eb5-108">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="85eb5-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="85eb5-109">Użyj wartości zero dla domyślny algorytm skrótu.</span><span class="sxs-lookup"><span data-stu-id="85eb5-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="85eb5-110">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="85eb5-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="85eb5-111">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="85eb5-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="85eb5-112">[out] Zwrócony rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="85eb5-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85eb5-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85eb5-113">Return Value</span></span>  
 <span data-ttu-id="85eb5-114">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="85eb5-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85eb5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85eb5-115">Requirements</span></span>  
 <span data-ttu-id="85eb5-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85eb5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85eb5-117">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="85eb5-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="85eb5-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85eb5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85eb5-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85eb5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85eb5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85eb5-120">See Also</span></span>  
 [<span data-ttu-id="85eb5-121">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="85eb5-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="85eb5-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="85eb5-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
