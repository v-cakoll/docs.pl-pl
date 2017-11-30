---
title: "IMetaDataImport::GetNameFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="9654b-102">IMetaDataImport::GetNameFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="9654b-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="9654b-103">Pobiera nazwę UTF-8 obiektu odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="9654b-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="9654b-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9654b-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9654b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9654b-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9654b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9654b-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="9654b-107">[in] Token reprezentujący obiekt, aby zwrócić nazwę.</span><span class="sxs-lookup"><span data-stu-id="9654b-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="9654b-108">[out] Wskaźnik do nazwy obiektu UTF-8 w stosie.</span><span class="sxs-lookup"><span data-stu-id="9654b-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9654b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9654b-109">Remarks</span></span>  
 <span data-ttu-id="9654b-110">`GetNameFromToken`jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="9654b-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="9654b-111">Alternatywnie, należy wywołać metodę można pobrać właściwości określonego rodzaju token wymagane, takie jak `GetFieldProps` dla pola lub `GetMethodProps` metody.</span><span class="sxs-lookup"><span data-stu-id="9654b-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9654b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9654b-112">Requirements</span></span>  
 <span data-ttu-id="9654b-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9654b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9654b-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9654b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9654b-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9654b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9654b-116">**Wersje programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="9654b-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9654b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9654b-117">See Also</span></span>  
 [<span data-ttu-id="9654b-118">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="9654b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9654b-119">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="9654b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
