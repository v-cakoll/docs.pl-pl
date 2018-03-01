---
title: "ICLRMetadataLocator::GetMetadata — Metoda"
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
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8758a96464d1465d92fb17314f1e36ab8d9169c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="e7b83-102">ICLRMetadataLocator::GetMetadata — Metoda</span><span class="sxs-lookup"><span data-stu-id="e7b83-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="e7b83-103">Metoda wywoływana przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) dostępu do usług danych do pobierania metadanych obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7b83-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7b83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7b83-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="e7b83-106">[in] Ciąg, który określa ścieżkę do pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="e7b83-107">[in] Sygnatura czasowa pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="e7b83-108">[in] Rozmiar pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="e7b83-109">[in] Globalnie unikatowy identyfikator obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="e7b83-110">[in] Wirtualny adres względny (RVA) metadanych.</span><span class="sxs-lookup"><span data-stu-id="e7b83-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="e7b83-111">Adres jest określany względem adresu podstawowego obrazu.</span><span class="sxs-lookup"><span data-stu-id="e7b83-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="e7b83-112">[in] Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e7b83-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="e7b83-113">[in] Rozmiar buforu, w której ma zostać umieszczony metadanych.</span><span class="sxs-lookup"><span data-stu-id="e7b83-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e7b83-114">[out] Bufor, w której ma zostać umieszczony metadanych.</span><span class="sxs-lookup"><span data-stu-id="e7b83-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="e7b83-115">[out] Rozmiar metadanych, który jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="e7b83-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7b83-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7b83-116">Remarks</span></span>  
 <span data-ttu-id="e7b83-117">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7b83-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b83-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7b83-118">Requirements</span></span>  
 <span data-ttu-id="e7b83-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7b83-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b83-120">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e7b83-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e7b83-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b83-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b83-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b83-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b83-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7b83-123">See Also</span></span>  
 [<span data-ttu-id="e7b83-124">ICLRMetadataLocator, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7b83-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
