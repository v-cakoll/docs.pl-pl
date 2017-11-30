---
title: "ImportFile — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a><span data-ttu-id="e0275-102">ImportFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0275-102">ImportFile Method</span></span>
<span data-ttu-id="e0275-103">Importuje zestawów i modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="e0275-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0275-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0275-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0275-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0275-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e0275-106">Pełna nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="e0275-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="e0275-107">Nazwa pliku wyjściowego opcjonalne, który może służyć do zmiany nazwy pliku, ponieważ jest on połączony w zestawie.</span><span class="sxs-lookup"><span data-stu-id="e0275-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="e0275-108">Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="e0275-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="e0275-109">Wskaźnik do tokenu, w którym będzie przechowywany Unikatowy identyfikator pliku.</span><span class="sxs-lookup"><span data-stu-id="e0275-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="e0275-110">Może to być plik zestawu lub pliku.</span><span class="sxs-lookup"><span data-stu-id="e0275-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="e0275-111">Odbiera Wskaźnik do [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e0275-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="e0275-112">Może mieć wartości NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="e0275-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="e0275-113">Wskaźnik do liczby plików i/lub zakresy, które zostały zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="e0275-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0275-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0275-114">Return Value</span></span>  
 <span data-ttu-id="e0275-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e0275-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0275-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0275-116">Requirements</span></span>  
 <span data-ttu-id="e0275-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="e0275-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0275-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0275-118">See Also</span></span>  
 [<span data-ttu-id="e0275-119">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0275-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e0275-120">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0275-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e0275-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="e0275-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
