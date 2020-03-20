---
title: IMetaDataAssemblyImport::FindExportedTypeByName — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175996"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="83c3a-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="83c3a-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="83c3a-103">Pobiera wskaźnik do typu eksportowanego, biorąc pod uwagę jego nazwę i otaczający typ.</span><span class="sxs-lookup"><span data-stu-id="83c3a-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83c3a-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83c3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83c3a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="83c3a-106">[w] Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="83c3a-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="83c3a-107">[w] Token metadanych dla otaczającej klasy eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="83c3a-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="83c3a-108">Ta wartość `mdExportedTypeNil` jest, jeśli żądany typ eksportowane nie jest typem zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="83c3a-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="83c3a-109">[na zewnątrz] Wskaźnik do `mdExportedType` tokenu, który reprezentuje eksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="83c3a-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c3a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83c3a-110">Remarks</span></span>  
 <span data-ttu-id="83c3a-111">Metoda `FindExportedTypeByName` używa standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="83c3a-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83c3a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83c3a-112">Requirements</span></span>  
 <span data-ttu-id="83c3a-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83c3a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83c3a-114">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="83c3a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83c3a-115">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83c3a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83c3a-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83c3a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c3a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83c3a-117">See also</span></span>

- [<span data-ttu-id="83c3a-118">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="83c3a-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="83c3a-119">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="83c3a-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
