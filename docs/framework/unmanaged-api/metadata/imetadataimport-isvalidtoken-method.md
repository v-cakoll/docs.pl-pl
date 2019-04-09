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
ms.openlocfilehash: 3a99ed42f500b83b5109631b21a88029995b43d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123884"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="14ee4-102">IMetaDataImport::IsValidToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="14ee4-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="14ee4-103">Pobiera wartość wskazującą, czy określony token zawiera prawidłowe odwołanie do obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="14ee4-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ee4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14ee4-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14ee4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14ee4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="14ee4-106">[in] Token do sprawdzania poprawności odwołania dla.</span><span class="sxs-lookup"><span data-stu-id="14ee4-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14ee4-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="14ee4-107">Return Value</span></span>  
 `true` <span data-ttu-id="14ee4-108">Jeśli `tk` jest tokenem poprawności metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="14ee4-108">if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="14ee4-109">W przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="14ee4-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ee4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14ee4-110">Requirements</span></span>  
 <span data-ttu-id="14ee4-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ee4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ee4-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="14ee4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14ee4-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14ee4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="14ee4-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="14ee4-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="14ee4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14ee4-115">See also</span></span>

- [<span data-ttu-id="14ee4-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14ee4-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="14ee4-117">IMetaDataImport2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="14ee4-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
