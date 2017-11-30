---
title: "ImportFileEx2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx2
helpviewer_keywords: ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2416a630f9bd763d4d4d31170cc606b160bb854
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex2-method"></a><span data-ttu-id="3c3d7-102">ImportFileEx2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="3c3d7-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="3c3d7-103">Importuje zestawów i modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="3c3d7-104">Ta metoda jest podobna [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale działa, nawet jeśli importowany plik nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c3d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c3d7-105">Syntax</span></span>  
  
```  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c3d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c3d7-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="3c3d7-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="3c3d7-108">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="3c3d7-109">Zakres opcjonalny import [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-109">Optional import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="3c3d7-110">Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3c3d7-111">Flagi są przekazywane do [OpenScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="3c3d7-111">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="3c3d7-112">Otrzymuje unikatowy identyfikator dla zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="3c3d7-113">Odbiera zakresu importu zestawu [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="3c3d7-114">Może mieć wartości NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="3c3d7-115">Odbiera liczbę plików i/lub zaimportowana zakresów.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c3d7-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3c3d7-116">Return Value</span></span>  
 <span data-ttu-id="3c3d7-117">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c3d7-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c3d7-118">Requirements</span></span>  
 <span data-ttu-id="3c3d7-119">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="3c3d7-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3d7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c3d7-120">See Also</span></span>  
 [<span data-ttu-id="3c3d7-121">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="3c3d7-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3c3d7-122">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="3c3d7-122">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3c3d7-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="3c3d7-123">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
