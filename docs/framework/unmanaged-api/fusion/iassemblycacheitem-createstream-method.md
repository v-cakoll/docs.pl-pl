---
title: IAssemblyCacheItem::CreateStream — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b3242e8ae29b9d21dc50d3ea0476967e9746f
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42752263"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="8a236-102">IAssemblyCacheItem::CreateStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a236-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="8a236-103">Tworzy strumień o określonej nazwie i format.</span><span class="sxs-lookup"><span data-stu-id="8a236-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a236-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a236-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a236-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a236-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="8a236-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="8a236-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="8a236-107">[in] Nazwa strumienia, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="8a236-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="8a236-108">[in] Format pliku do celów przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="8a236-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="8a236-109">[in] Zdefiniowane w Fusion.idl flagi specyficzne dla formatu.</span><span class="sxs-lookup"><span data-stu-id="8a236-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="8a236-110">[out] Wskaźnik na adres zwracanego [IStream](/windows/desktop/api/objidl/nn-objidl-istream) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8a236-110">[out] A pointer to the address of the returned [IStream](/windows/desktop/api/objidl/nn-objidl-istream) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="8a236-111">[in, opcjonalny] Maksymalny rozmiar strumienia odwołuje się `ppIStream`.</span><span class="sxs-lookup"><span data-stu-id="8a236-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a236-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a236-112">Requirements</span></span>  
 <span data-ttu-id="8a236-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a236-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a236-114">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8a236-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8a236-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a236-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a236-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a236-116">See Also</span></span>  
 [<span data-ttu-id="8a236-117">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a236-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
