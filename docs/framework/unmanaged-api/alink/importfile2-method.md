---
title: ImportFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFile2
helpviewer_keywords:
- ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3c145bae61922894f4893d532923319ccf16f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499015"
---
# <a name="importfile2-method"></a><span data-ttu-id="07f81-102">ImportFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="07f81-102">ImportFile2 Method</span></span>
<span data-ttu-id="07f81-103">Importuje zestawów i modułów niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="07f81-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="07f81-104">Ta metoda przypomina [importfile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale wtedy, gdy importowanego pliku nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="07f81-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07f81-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="07f81-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07f81-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="07f81-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="07f81-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="07f81-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="07f81-108">Nazwa pliku wyjściowego opcjonalny, którego można zmienić nazwy pliku, ponieważ jest on połączony do zestawu.</span><span class="sxs-lookup"><span data-stu-id="07f81-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="07f81-109">Opcjonalne zakresu [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="07f81-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="07f81-110">W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="07f81-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="07f81-111">Odbiera identyfikator pliku lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="07f81-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="07f81-112">Odbiera [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="07f81-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="07f81-113">Wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="07f81-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="07f81-114">Odbiera znaleziono plików i/lub zakresów zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="07f81-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07f81-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="07f81-115">Return Value</span></span>  
 <span data-ttu-id="07f81-116">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="07f81-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07f81-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07f81-117">Requirements</span></span>  
 <span data-ttu-id="07f81-118">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="07f81-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f81-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07f81-119">See also</span></span>
- [<span data-ttu-id="07f81-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="07f81-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="07f81-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="07f81-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="07f81-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="07f81-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
