---
title: IMetaDataConverter::GetTypeLibFromMetaData — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: ef573eb9a572c27e685289b2740a55e898be2093
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177631"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="8104a-102">IMetaDataConverter::GetTypeLibFromMetaData — Metoda</span><span class="sxs-lookup"><span data-stu-id="8104a-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>
<span data-ttu-id="8104a-103">Pobiera wskaźnik do `ITypeLib` wystąpienia, który reprezentuje bibliotekę typów, która ma określone nazwy biblioteki i modułów.</span><span class="sxs-lookup"><span data-stu-id="8104a-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8104a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8104a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8104a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8104a-105">Parameters</span></span>  
 `strModule`  
 <span data-ttu-id="8104a-106">[w] Nazwa modułu biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8104a-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="8104a-107">[w] Nazwa biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8104a-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="8104a-108">[na zewnątrz] Wskaźnik do lokalizacji, która odbiera `ITypeLib` adres wystąpienia, które reprezentuje bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="8104a-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8104a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8104a-109">Requirements</span></span>  
 <span data-ttu-id="8104a-110">**Platforma:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8104a-110">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8104a-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="8104a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8104a-112">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8104a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8104a-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8104a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8104a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8104a-114">See also</span></span>

- [<span data-ttu-id="8104a-115">IMetaDataConverter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8104a-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)
