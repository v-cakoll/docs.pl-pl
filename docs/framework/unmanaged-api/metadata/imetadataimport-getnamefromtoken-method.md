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
ms.openlocfilehash: 1d77891478c9136a18dc4c9c44beed805244dd1a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225940"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="88622-102">IMetaDataImport::GetNameFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="88622-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="88622-103">Pobiera nazwę UTF-8 zawiera odwołanie do tokenu metadanych określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="88622-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="88622-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="88622-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88622-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="88622-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88622-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="88622-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="88622-107">[in] Token reprezentujący obiekt, aby zwrócić nazwę.</span><span class="sxs-lookup"><span data-stu-id="88622-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="88622-108">[out] Wskaźnik do nazwy obiektu UTF-8 w stosie.</span><span class="sxs-lookup"><span data-stu-id="88622-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88622-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88622-109">Remarks</span></span>  
 `GetNameFromToken` <span data-ttu-id="88622-110">jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="88622-110">is obsolete.</span></span> <span data-ttu-id="88622-111">Alternatywnie należy wywołać metodę można pobrać właściwości określonego rodzaju token jest wymagany, takich jak `GetFieldProps` dla pola lub `GetMethodProps` dla metody.</span><span class="sxs-lookup"><span data-stu-id="88622-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88622-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88622-112">Requirements</span></span>  
 <span data-ttu-id="88622-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88622-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88622-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="88622-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="88622-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88622-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88622-116">**Wersje programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="88622-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88622-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88622-117">See also</span></span>

- [<span data-ttu-id="88622-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="88622-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="88622-119">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="88622-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
