---
title: "ImportFileEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71a7bc1ba9f23f1c581ca3528752e04003d9857c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="bbfb3-102">ImportFileEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="bbfb3-102">ImportFileEx Method</span></span>
<span data-ttu-id="bbfb3-103">Importy wskazane zestawu lub modułu niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbfb3-104">Syntax</span></span>  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbfb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbfb3-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="bbfb3-106">Pełna nazwa pliku, z którego będą importowane.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="bbfb3-107">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="bbfb3-108">Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="bbfb3-109">Flagi są przekazywane do [OpenScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="bbfb3-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="bbfb3-110">Odbiera identyfikator importowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="bbfb3-111">Odbiera zakresu importu zestawu [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="bbfb3-112">Jest ustawiony na wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="bbfb3-113">Odbiera liczba importowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbfb3-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bbfb3-114">Return Value</span></span>  
 <span data-ttu-id="bbfb3-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfb3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbfb3-116">Requirements</span></span>  
 <span data-ttu-id="bbfb3-117">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="bbfb3-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfb3-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbfb3-118">See Also</span></span>  
 [<span data-ttu-id="bbfb3-119">Ialink2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="bbfb3-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bbfb3-120">Ialink — interfejs</span><span class="sxs-lookup"><span data-stu-id="bbfb3-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bbfb3-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="bbfb3-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
