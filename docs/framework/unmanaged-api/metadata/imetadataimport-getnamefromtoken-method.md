---
title: IMetaDataImport::GetNameFromToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a39eac88537d47535844d1f05e0741cc94142f0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="1ccf2-102">IMetaDataImport::GetNameFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ccf2-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="1ccf2-103">Pobiera nazwę UTF-8 obiektu odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="1ccf2-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ccf2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ccf2-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ccf2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ccf2-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1ccf2-107">[in] Token reprezentujący obiekt, aby zwrócić nazwę.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="1ccf2-108">[out] Wskaźnik do nazwy obiektu UTF-8 w stosie.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ccf2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ccf2-109">Remarks</span></span>  
 <span data-ttu-id="1ccf2-110">`GetNameFromToken` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="1ccf2-111">Alternatywnie, należy wywołać metodę można pobrać właściwości określonego rodzaju token wymagane, takie jak `GetFieldProps` dla pola lub `GetMethodProps` metody.</span><span class="sxs-lookup"><span data-stu-id="1ccf2-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ccf2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ccf2-112">Requirements</span></span>  
 <span data-ttu-id="1ccf2-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ccf2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ccf2-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ccf2-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ccf2-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ccf2-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ccf2-116">**Wersje programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="1ccf2-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ccf2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ccf2-117">See Also</span></span>  
 [<span data-ttu-id="1ccf2-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ccf2-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1ccf2-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ccf2-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
