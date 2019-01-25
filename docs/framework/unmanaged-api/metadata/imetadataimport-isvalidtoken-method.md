---
title: IMetaDataImport::IsValidToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a9e5a2f7baa1c15ac54950bf1bfc0d448d08f58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567798"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="f23aa-102">IMetaDataImport::IsValidToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="f23aa-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="f23aa-103">Pobiera wartość wskazującą, czy określony token zawiera prawidłowe odwołanie do obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="f23aa-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f23aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f23aa-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f23aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f23aa-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f23aa-106">[in] Token do sprawdzania poprawności odwołania dla.</span><span class="sxs-lookup"><span data-stu-id="f23aa-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f23aa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f23aa-107">Return Value</span></span>  
 <span data-ttu-id="f23aa-108">`true` Jeśli `tk` jest tokenem poprawności metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="f23aa-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="f23aa-109">W przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="f23aa-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f23aa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f23aa-110">Requirements</span></span>  
 <span data-ttu-id="f23aa-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f23aa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f23aa-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f23aa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f23aa-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f23aa-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f23aa-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f23aa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f23aa-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f23aa-115">See also</span></span>
- [<span data-ttu-id="f23aa-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f23aa-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f23aa-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f23aa-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
