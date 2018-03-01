---
title: "GetHashFromAssemblyFileW — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 938d7b5633a73aafb81b16fd2fa207160cac4e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="84fef-102">GetHashFromAssemblyFileW — Funkcja</span><span class="sxs-lookup"><span data-stu-id="84fef-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="84fef-103">Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="84fef-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="84fef-104">Ścieżka do pliku zestawu muszą być określone jako ciąg Unicode.</span><span class="sxs-lookup"><span data-stu-id="84fef-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="84fef-105">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="84fef-105">This function has been deprecated.</span></span> <span data-ttu-id="84fef-106">Użyj [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="84fef-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84fef-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="84fef-107">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84fef-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="84fef-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="84fef-109">[in] Ścieżka do pliku, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="84fef-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="84fef-110">Ten parametr musi być ciągiem Unicode.</span><span class="sxs-lookup"><span data-stu-id="84fef-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="84fef-111">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="84fef-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="84fef-112">Użyj wartości zero dla domyślny algorytm skrótu.</span><span class="sxs-lookup"><span data-stu-id="84fef-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="84fef-113">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="84fef-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="84fef-114">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="84fef-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="84fef-115">[out] Zwrócony rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="84fef-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84fef-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84fef-116">Requirements</span></span>  
 <span data-ttu-id="84fef-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84fef-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84fef-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="84fef-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="84fef-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84fef-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84fef-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84fef-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fef-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84fef-121">See Also</span></span>  
 [<span data-ttu-id="84fef-122">GetHashFromAssemblyFileW, metoda</span><span class="sxs-lookup"><span data-stu-id="84fef-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="84fef-123">GetHashFromAssemblyFile, metoda</span><span class="sxs-lookup"><span data-stu-id="84fef-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="84fef-124">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="84fef-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
