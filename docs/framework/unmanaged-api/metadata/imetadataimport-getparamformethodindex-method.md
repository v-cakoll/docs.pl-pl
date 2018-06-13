---
title: IMetaDataImport::GetParamForMethodIndex — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31096f7a5fd23bbd54f2beb9258c9d529e94f373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448765"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="3a1bb-102">IMetaDataImport::GetParamForMethodIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a1bb-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="3a1bb-103">Pobiera token, który reprezentuje określony parametr metody reprezentowany przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a1bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a1bb-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a1bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a1bb-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="3a1bb-106">[in] Token, który reprezentuje metodę, aby zwrócić token parametr dla.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="3a1bb-107">[in] {Numer porządkowy pozycja na liście parametrów gdzie występuje żądanego parametru.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="3a1bb-108">Parametry są numerowane, począwszy od jednej z wartości zwracanej przez metodę w pozycji zero.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="3a1bb-109">[out] Wskaźnik do ParamDef token, który reprezentuje żądany parametr.</span><span class="sxs-lookup"><span data-stu-id="3a1bb-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a1bb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a1bb-110">Requirements</span></span>  
 <span data-ttu-id="3a1bb-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a1bb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a1bb-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3a1bb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3a1bb-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a1bb-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3a1bb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a1bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a1bb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a1bb-115">See Also</span></span>  
 [<span data-ttu-id="3a1bb-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a1bb-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3a1bb-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a1bb-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
