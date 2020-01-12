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
ms.openlocfilehash: c7f04364cc52bd38d7d2659d1d188c5fd783ad01
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899760"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="3a4a2-102">ICLRStrongName::StrongNameGetBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a4a2-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="3a4a2-103">Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="3a4a2-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a4a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a4a2-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a4a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a4a2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3a4a2-106">podczas Prawidłowa ścieżka do pliku wykonywalnego, który ma zostać załadowany.</span><span class="sxs-lookup"><span data-stu-id="3a4a2-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="3a4a2-107">podczas Bufor, do którego ma zostać załadowany plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="3a4a2-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="3a4a2-108">[in. out] Żądany maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="3a4a2-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="3a4a2-109">Po powrocie, rzeczywisty rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="3a4a2-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a4a2-110">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="3a4a2-110">Return Value</span></span>  
 <span data-ttu-id="3a4a2-111">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="3a4a2-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a4a2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a4a2-112">Requirements</span></span>  
 <span data-ttu-id="3a4a2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a4a2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a4a2-114">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="3a4a2-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3a4a2-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3a4a2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a4a2-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a4a2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4a2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a4a2-117">See also</span></span>

- [<span data-ttu-id="3a4a2-118">StrongNameGetBlobFromImage, metoda</span><span class="sxs-lookup"><span data-stu-id="3a4a2-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="3a4a2-119">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a4a2-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
