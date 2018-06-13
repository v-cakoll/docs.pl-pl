---
title: ICLRStrongName::GetHashFromAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95fbab459355c237157d43cee0211e42f6d26c62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432628"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="9364f-102">ICLRStrongName::GetHashFromAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="9364f-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="9364f-103">Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="9364f-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9364f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9364f-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9364f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9364f-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="9364f-106">[in] Ścieżka do pliku, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="9364f-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9364f-107">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="9364f-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9364f-108">Użyj wartości zero dla domyślny algorytm skrótu.</span><span class="sxs-lookup"><span data-stu-id="9364f-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9364f-109">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="9364f-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9364f-110">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9364f-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9364f-111">[out] Zwrócony rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9364f-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9364f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9364f-112">Return Value</span></span>  
 <span data-ttu-id="9364f-113">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="9364f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9364f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9364f-114">Requirements</span></span>  
 <span data-ttu-id="9364f-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9364f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9364f-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9364f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9364f-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9364f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9364f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9364f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9364f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9364f-119">See Also</span></span>  
 [<span data-ttu-id="9364f-120">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="9364f-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="9364f-121">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="9364f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
