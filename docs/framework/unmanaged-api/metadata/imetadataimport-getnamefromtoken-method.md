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
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437274"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="094ec-102">IMetaDataImport::GetNameFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="094ec-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="094ec-103">Pobiera nazwę UTF-8 obiektu, do którego odwołuje się określony token metadanych.</span><span class="sxs-lookup"><span data-stu-id="094ec-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="094ec-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="094ec-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="094ec-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="094ec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="094ec-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="094ec-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="094ec-107">podczas Token reprezentujący obiekt, dla którego ma zostać zwrócona nazwa.</span><span class="sxs-lookup"><span data-stu-id="094ec-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="094ec-108">określoną Wskaźnik do nazwy obiektu UTF-8 w stercie.</span><span class="sxs-lookup"><span data-stu-id="094ec-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="094ec-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="094ec-109">Remarks</span></span>  
 <span data-ttu-id="094ec-110">`GetNameFromToken` jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="094ec-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="094ec-111">Alternatywnie Wywołaj metodę, aby uzyskać właściwości określonego typu wymaganego tokenu, takie jak `GetFieldProps` dla pola lub `GetMethodProps` dla metody.</span><span class="sxs-lookup"><span data-stu-id="094ec-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="094ec-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="094ec-112">Requirements</span></span>  
 <span data-ttu-id="094ec-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="094ec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="094ec-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="094ec-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="094ec-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="094ec-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="094ec-116">**.NET Framework wersje:** 1,0</span><span class="sxs-lookup"><span data-stu-id="094ec-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="094ec-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="094ec-117">See also</span></span>

- [<span data-ttu-id="094ec-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="094ec-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="094ec-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="094ec-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
