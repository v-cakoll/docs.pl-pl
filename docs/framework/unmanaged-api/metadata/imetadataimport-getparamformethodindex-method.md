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
ms.openlocfilehash: 7455d87caff86c57409f4bb016ec73c365a3d35d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487125"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="7dc5d-102">IMetaDataImport::GetParamForMethodIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="7dc5d-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="7dc5d-103">Pobiera token, który reprezentuje określony parametr metody reprezentowanej przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="7dc5d-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dc5d-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dc5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dc5d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="7dc5d-106">[in] Token, który reprezentuje metodę do zwracania tokenu parametr dla.</span><span class="sxs-lookup"><span data-stu-id="7dc5d-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="7dc5d-107">[in] Numer porządkowy pozycja na liście parametrów realizowana żądanego parametru.</span><span class="sxs-lookup"><span data-stu-id="7dc5d-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="7dc5d-108">Parametry są ponumerowane, zaczynając od jednego z wartością zwracaną metody w pozycji zero.</span><span class="sxs-lookup"><span data-stu-id="7dc5d-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="7dc5d-109">[out] Wskaźnik do tokenu ParamDef, który reprezentuje żądany parametr.</span><span class="sxs-lookup"><span data-stu-id="7dc5d-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dc5d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dc5d-110">Requirements</span></span>  
 <span data-ttu-id="7dc5d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dc5d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dc5d-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7dc5d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dc5d-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7dc5d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dc5d-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dc5d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc5d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dc5d-115">See also</span></span>
- [<span data-ttu-id="7dc5d-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7dc5d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7dc5d-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7dc5d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
