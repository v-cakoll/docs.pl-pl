---
title: IMetaDataImport::GetTypeRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25482ee81d5210e5ab69007767aecf01435602d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448599"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="9f513-102">IMetaDataImport::GetTypeRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f513-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="9f513-103">Pobiera metadane skojarzone z <xref:System.Type> odwołuje się określony token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="9f513-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f513-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f513-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f513-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f513-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="9f513-106">[in] Token TypeRef, który reprezentuje typ do zwrócenia metadanych.</span><span class="sxs-lookup"><span data-stu-id="9f513-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="9f513-107">[out] Wskaźnik do zakresu, w którym odniesienia.</span><span class="sxs-lookup"><span data-stu-id="9f513-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="9f513-108">Ta wartość jest token elementu AssemblyRef lub element ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="9f513-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="9f513-109">[out] Bufor zawierający nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="9f513-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9f513-110">[in] Żądany rozmiar w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="9f513-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9f513-111">[out] Rozmiar zwróconego w znaki dwubajtowe `szName`.</span><span class="sxs-lookup"><span data-stu-id="9f513-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f513-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f513-112">Requirements</span></span>  
 <span data-ttu-id="9f513-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f513-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f513-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f513-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f513-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f513-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f513-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f513-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f513-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f513-117">See Also</span></span>  
 [<span data-ttu-id="9f513-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f513-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9f513-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9f513-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
