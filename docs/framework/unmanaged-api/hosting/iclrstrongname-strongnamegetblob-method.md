---
title: ICLRStrongName::StrongNameGetBlob — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4621a7d143d401d4cb620ac17c31e4ee5f13837
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086778"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="7e8a1-102">ICLRStrongName::StrongNameGetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e8a1-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="7e8a1-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="7e8a1-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e8a1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e8a1-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e8a1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e8a1-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7e8a1-106">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="7e8a1-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="7e8a1-107">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="7e8a1-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="7e8a1-108">[out w] Maksymalny rozmiar w bajtach, żądane `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7e8a1-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="7e8a1-109">Po powrocie, rzeczywisty rozmiar w bajtach, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7e8a1-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e8a1-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7e8a1-110">Return Value</span></span>  
 <span data-ttu-id="7e8a1-111">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="7e8a1-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e8a1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e8a1-112">Requirements</span></span>  
 <span data-ttu-id="7e8a1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e8a1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e8a1-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7e8a1-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7e8a1-115">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e8a1-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e8a1-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e8a1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e8a1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e8a1-117">See Also</span></span>  
 [<span data-ttu-id="7e8a1-118">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="7e8a1-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="7e8a1-119">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e8a1-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
