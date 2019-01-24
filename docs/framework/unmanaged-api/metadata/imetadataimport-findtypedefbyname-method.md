---
title: IMetaDataImport::FindTypeDefByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b6040f21bb530ce775fc79e33b97eb14870c04f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578827"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="02383-102">IMetaDataImport::FindTypeDefByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="02383-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="02383-103">Pobiera wskaźnik do metadanych TypeDef tokenu do <xref:System.Type> o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="02383-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02383-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02383-104">Syntax</span></span>  
  
```  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02383-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02383-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="02383-106">[in] Nazwa typu, dla którego można uzyskać tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="02383-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="02383-107">[in] Element TypeDef lub TypeRef token reprezentujący otaczającej klasy.</span><span class="sxs-lookup"><span data-stu-id="02383-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="02383-108">Jeśli typ do znalezienia nie jest klasą zagnieżdżoną, wartość tę należy ustawić na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="02383-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="02383-109">[out] Wskaźnik do zgodnego tokenu TypeDef.</span><span class="sxs-lookup"><span data-stu-id="02383-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02383-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02383-110">Requirements</span></span>  
 <span data-ttu-id="02383-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02383-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02383-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="02383-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02383-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02383-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02383-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02383-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02383-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02383-115">See also</span></span>
- [<span data-ttu-id="02383-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="02383-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02383-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="02383-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
