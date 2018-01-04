---
title: "ImportFile2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ce7433745bb76a6c12e60e11e02cd1e7ef156614
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="importfile2-method"></a><span data-ttu-id="81bd2-102">ImportFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="81bd2-102">ImportFile2 Method</span></span>
<span data-ttu-id="81bd2-103">Importuje zestawów i modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="81bd2-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="81bd2-104">Ta metoda jest podobna [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), ale działa, nawet jeśli importowany plik nie istnieje na dysku.</span><span class="sxs-lookup"><span data-stu-id="81bd2-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bd2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="81bd2-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="81bd2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="81bd2-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="81bd2-107">Nazwa pliku do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="81bd2-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="81bd2-108">Nazwa pliku wyjściowego opcjonalne, który może służyć do zmiany nazwy pliku, ponieważ jest on połączony w zestawie.</span><span class="sxs-lookup"><span data-stu-id="81bd2-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="81bd2-109">Opcjonalne zakresu [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="81bd2-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="81bd2-110">Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="81bd2-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="81bd2-111">Odbiera identyfikator pliku lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="81bd2-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="81bd2-112">Odbiera [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="81bd2-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="81bd2-113">Wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="81bd2-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="81bd2-114">Odbiera znaleziono plików i/lub zaimportowana zakresów.</span><span class="sxs-lookup"><span data-stu-id="81bd2-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81bd2-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81bd2-115">Return Value</span></span>  
 <span data-ttu-id="81bd2-116">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="81bd2-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81bd2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81bd2-117">Requirements</span></span>  
 <span data-ttu-id="81bd2-118">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="81bd2-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bd2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81bd2-119">See Also</span></span>  
 [<span data-ttu-id="81bd2-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="81bd2-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="81bd2-121">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="81bd2-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="81bd2-122">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="81bd2-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
