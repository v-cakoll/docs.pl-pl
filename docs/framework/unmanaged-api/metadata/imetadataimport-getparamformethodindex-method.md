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
ms.openlocfilehash: a70691b9c519bc59ae7df7a86d5d6697db565575
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437163"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="3e8f9-102">IMetaDataImport::GetParamForMethodIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="3e8f9-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="3e8f9-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="3e8f9-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e8f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e8f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e8f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3e8f9-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="3e8f9-106">[in] A token that represents the method to return the parameter token for.</span><span class="sxs-lookup"><span data-stu-id="3e8f9-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="3e8f9-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span><span class="sxs-lookup"><span data-stu-id="3e8f9-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="3e8f9-108">Parameters are numbered starting from one, with the method's return value in position zero.</span><span class="sxs-lookup"><span data-stu-id="3e8f9-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="3e8f9-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span><span class="sxs-lookup"><span data-stu-id="3e8f9-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e8f9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3e8f9-110">Requirements</span></span>  
 <span data-ttu-id="3e8f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e8f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e8f9-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3e8f9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e8f9-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e8f9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e8f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e8f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8f9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e8f9-115">See also</span></span>

- [<span data-ttu-id="3e8f9-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e8f9-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3e8f9-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3e8f9-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
