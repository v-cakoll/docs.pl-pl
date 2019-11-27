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
ms.openlocfilehash: 3e470250fa0e86610fcc9a6d6e2ca03569d62b54
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449447"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="7a27e-102">IMetaDataAssemblyImport::FindExportedTypeByName — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a27e-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="7a27e-103">Pobiera wskaźnik do wyeksportowanego typu z uwzględnieniem jego nazwy i typu otaczającego.</span><span class="sxs-lookup"><span data-stu-id="7a27e-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a27e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a27e-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,   
    [in]  mdToken           mdtExportedType,   
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a27e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a27e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="7a27e-106">podczas Nazwa wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="7a27e-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="7a27e-107">podczas Token metadanych dla otaczającej klasy wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="7a27e-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="7a27e-108">Ta wartość jest `mdExportedTypeNil`, jeśli żądany wyeksportowany typ nie jest typem zagnieżdżonym.</span><span class="sxs-lookup"><span data-stu-id="7a27e-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="7a27e-109">określoną Wskaźnik do tokenu `mdExportedType`, który reprezentuje wyeksportowany typ.</span><span class="sxs-lookup"><span data-stu-id="7a27e-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a27e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a27e-110">Remarks</span></span>  
 <span data-ttu-id="7a27e-111">Metoda `FindExportedTypeByName` używa standardowych reguł używanych przez środowisko uruchomieniowe języka wspólnego do rozpoznawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="7a27e-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a27e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a27e-112">Requirements</span></span>  
 <span data-ttu-id="7a27e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a27e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a27e-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7a27e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a27e-115">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7a27e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a27e-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a27e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a27e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a27e-117">See also</span></span>

- [<span data-ttu-id="7a27e-118">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a27e-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7a27e-119">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7a27e-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
