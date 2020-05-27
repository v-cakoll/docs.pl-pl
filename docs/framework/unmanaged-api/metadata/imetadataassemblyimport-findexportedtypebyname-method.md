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
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009395"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="5faa3-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="5faa3-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="5faa3-103">Pobiera wskaźnik do wyeksportowanego typu z uwzględnieniem jego nazwy i typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="5faa3-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5faa3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5faa3-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5faa3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5faa3-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="5faa3-106">podczas Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="5faa3-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="5faa3-107">podczas Token metadanych dla otaczającej klasy wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="5faa3-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="5faa3-108">Ta wartość jest `mdExportedTypeNil` , jeśli żądany wyeksportowany typ nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="5faa3-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="5faa3-109">określoną Wskaźnik do `mdExportedType` tokenu, który reprezentuje wyeksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="5faa3-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5faa3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5faa3-110">Remarks</span></span>  
 <span data-ttu-id="5faa3-111">`FindExportedTypeByName`Metoda używa standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="5faa3-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5faa3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5faa3-112">Requirements</span></span>  
 <span data-ttu-id="5faa3-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5faa3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5faa3-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5faa3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5faa3-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5faa3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5faa3-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5faa3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faa3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5faa3-117">See also</span></span>

- [<span data-ttu-id="5faa3-118">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5faa3-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="5faa3-119">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5faa3-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
