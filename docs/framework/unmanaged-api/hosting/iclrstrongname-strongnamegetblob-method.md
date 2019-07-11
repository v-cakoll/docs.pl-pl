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
ms.openlocfilehash: cbc0262062eddb363b0a00535a2d099100124b67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748077"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="aa552-102">ICLRStrongName::StrongNameGetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa552-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="aa552-103">Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="aa552-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa552-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa552-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa552-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa552-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="aa552-106">[in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.</span><span class="sxs-lookup"><span data-stu-id="aa552-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="aa552-107">[in] Bufor, do którego można załadować pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="aa552-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="aa552-108">[out w] Maksymalny rozmiar w bajtach, żądane `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="aa552-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="aa552-109">Po powrocie, rzeczywisty rozmiar w bajtach, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="aa552-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa552-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa552-110">Return Value</span></span>  
 <span data-ttu-id="aa552-111">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="aa552-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa552-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa552-112">Requirements</span></span>  
 <span data-ttu-id="aa552-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa552-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa552-114">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aa552-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aa552-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa552-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa552-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa552-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa552-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa552-117">See also</span></span>

- [<span data-ttu-id="aa552-118">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="aa552-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="aa552-119">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa552-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
