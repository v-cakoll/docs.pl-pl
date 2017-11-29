---
title: "IMetaDataImport::GetParamForMethodIndex — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamForMethodIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda4ffde7d38d74ddf7a81b6f0af4a556693094d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="5aeb6-102">IMetaDataImport::GetParamForMethodIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="5aeb6-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="5aeb6-103">Pobiera token, który reprezentuje określony parametr metody reprezentowany przez określony token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aeb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5aeb6-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5aeb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aeb6-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="5aeb6-106">[in] Token, który reprezentuje metodę, aby zwrócić token parametr dla.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="5aeb6-107">[in] {Numer porządkowy pozycja na liście parametrów gdzie występuje żądanego parametru.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="5aeb6-108">Parametry są numerowane, począwszy od jednej z wartości zwracanej przez metodę w pozycji zero.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="5aeb6-109">[out] Wskaźnik do ParamDef token, który reprezentuje żądany parametr.</span><span class="sxs-lookup"><span data-stu-id="5aeb6-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aeb6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5aeb6-110">Requirements</span></span>  
 <span data-ttu-id="5aeb6-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aeb6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aeb6-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5aeb6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5aeb6-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5aeb6-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5aeb6-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aeb6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aeb6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5aeb6-115">See Also</span></span>  
 [<span data-ttu-id="5aeb6-116">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="5aeb6-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5aeb6-117">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5aeb6-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
