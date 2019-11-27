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
ms.openlocfilehash: edf24de8ae38aab97e41a53cc86ae5aa6c592c50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434692"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="6c428-102">IMetaDataImport::IsValidToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c428-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="6c428-103">Pobiera wartość wskazującą, czy określony token przechowuje prawidłowe odwołanie do obiektu kodu.</span><span class="sxs-lookup"><span data-stu-id="6c428-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c428-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c428-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c428-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c428-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6c428-106">podczas Token, aby sprawdzić prawidłowość odwołania.</span><span class="sxs-lookup"><span data-stu-id="6c428-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c428-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c428-107">Return Value</span></span>  
 <span data-ttu-id="6c428-108">`true`, jeśli `tk` jest prawidłowym tokenem metadanych w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6c428-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="6c428-109">W przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6c428-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c428-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c428-110">Requirements</span></span>  
 <span data-ttu-id="6c428-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c428-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c428-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c428-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c428-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c428-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c428-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c428-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c428-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c428-115">See also</span></span>

- [<span data-ttu-id="6c428-116">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c428-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6c428-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c428-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
