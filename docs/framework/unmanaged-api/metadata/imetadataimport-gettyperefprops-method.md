---
title: "IMetaDataImport::GetTypeRefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55cb1d9eac13fc2d6d788eff039c4528e627ff12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="4c62d-102">IMetaDataImport::GetTypeRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c62d-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="4c62d-103">Pobiera metadane skojarzone z <xref:System.Type> odwołuje się określony token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="4c62d-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c62d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c62d-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c62d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c62d-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="4c62d-106">[in] Token TypeRef, który reprezentuje typ do zwrócenia metadanych.</span><span class="sxs-lookup"><span data-stu-id="4c62d-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="4c62d-107">[out] Wskaźnik do zakresu, w którym odniesienia.</span><span class="sxs-lookup"><span data-stu-id="4c62d-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="4c62d-108">Ta wartość jest token elementu AssemblyRef lub element ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="4c62d-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="4c62d-109">[out] Bufor zawierający nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="4c62d-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4c62d-110">[in] Żądany rozmiar w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="4c62d-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4c62d-111">[out] Rozmiar zwróconego w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="4c62d-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c62d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c62d-112">Requirements</span></span>  
 <span data-ttu-id="4c62d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c62d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c62d-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c62d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c62d-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c62d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c62d-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c62d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c62d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c62d-117">See Also</span></span>  
 [<span data-ttu-id="4c62d-118">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="4c62d-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4c62d-119">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="4c62d-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
