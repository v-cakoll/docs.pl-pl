---
title: "GetHashFromAssemblyFile — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromAssemblyFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromAssemblyFile
helpviewer_keywords: GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1598e4e332525f87392ae5b0ad486a735e760651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="59fb9-102">GetHashFromAssemblyFile — Funkcja</span><span class="sxs-lookup"><span data-stu-id="59fb9-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="59fb9-103">Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="59fb9-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="59fb9-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="59fb9-104">This function has been deprecated.</span></span> <span data-ttu-id="59fb9-105">Użyj [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="59fb9-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59fb9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="59fb9-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59fb9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="59fb9-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="59fb9-108">[in] Ścieżka do pliku, aby być mieszany.</span><span class="sxs-lookup"><span data-stu-id="59fb9-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="59fb9-109">[w, out] Stała, który określa algorytm wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="59fb9-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="59fb9-110">Użyj wartości zero dla domyślny algorytm skrótu.</span><span class="sxs-lookup"><span data-stu-id="59fb9-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="59fb9-111">[out] Bufor zwrócony wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="59fb9-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="59fb9-112">[in] Maksymalny rozmiar żądanej z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="59fb9-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="59fb9-113">[out] Zwrócony rozmiar w bajtach z `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="59fb9-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59fb9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59fb9-114">Requirements</span></span>  
 <span data-ttu-id="59fb9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59fb9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59fb9-116">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="59fb9-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="59fb9-117">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59fb9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59fb9-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59fb9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fb9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59fb9-119">See Also</span></span>  
 [<span data-ttu-id="59fb9-120">GetHashFromAssemblyFile — metoda</span><span class="sxs-lookup"><span data-stu-id="59fb9-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="59fb9-121">GetHashFromAssemblyFileW — metoda</span><span class="sxs-lookup"><span data-stu-id="59fb9-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="59fb9-122">ICLRStrongName — interfejs</span><span class="sxs-lookup"><span data-stu-id="59fb9-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
