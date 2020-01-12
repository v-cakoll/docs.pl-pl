---
title: ICLRStrongName::StrongNameGetBlobFromImage — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: a0bcc62a1715fb455f0affee64a351cabe0ba3f6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901122"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="995bc-102">ICLRStrongName::StrongNameGetBlobFromImage — Metoda</span><span class="sxs-lookup"><span data-stu-id="995bc-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="995bc-103">Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.</span><span class="sxs-lookup"><span data-stu-id="995bc-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="995bc-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="995bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="995bc-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="995bc-106">podczas Adres pamięci mapowanego manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="995bc-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="995bc-107">podczas Rozmiar, w bajtach, obrazu w `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="995bc-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="995bc-108">podczas Bufor zawierający reprezentację binarną obrazu.</span><span class="sxs-lookup"><span data-stu-id="995bc-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="995bc-109">[in. out] Żądany maksymalny rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="995bc-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="995bc-110">Po powrocie, rzeczywisty rozmiar w bajtach `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="995bc-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="995bc-111">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="995bc-111">Return Value</span></span>  
 <span data-ttu-id="995bc-112">`S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).</span><span class="sxs-lookup"><span data-stu-id="995bc-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="995bc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="995bc-113">Requirements</span></span>  
 <span data-ttu-id="995bc-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="995bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="995bc-115">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="995bc-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="995bc-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="995bc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="995bc-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="995bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995bc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="995bc-118">See also</span></span>

- [<span data-ttu-id="995bc-119">StrongNameGetBlob, metoda</span><span class="sxs-lookup"><span data-stu-id="995bc-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="995bc-120">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="995bc-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
