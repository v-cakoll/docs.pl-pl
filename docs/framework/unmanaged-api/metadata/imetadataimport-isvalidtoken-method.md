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
ms.openlocfilehash: d752d6dbe8a6b7a23faae498f9118c8d89e92929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447700"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="32350-102">IMetaDataImport::IsValidToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="32350-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="32350-103">Pobiera wartość wskazującą, czy określony token jest prawidłowym odwołaniem do obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="32350-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32350-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32350-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32350-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32350-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="32350-106">[in] Token, aby sprawdzić poprawność odwołania dla.</span><span class="sxs-lookup"><span data-stu-id="32350-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32350-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="32350-107">Return Value</span></span>  
 <span data-ttu-id="32350-108">`true` Jeśli `tk` jest tokenem prawidłowe metadane w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="32350-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="32350-109">W przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="32350-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32350-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32350-110">Requirements</span></span>  
 <span data-ttu-id="32350-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32350-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32350-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32350-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32350-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32350-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32350-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32350-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32350-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32350-115">See Also</span></span>  
 [<span data-ttu-id="32350-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="32350-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="32350-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="32350-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
