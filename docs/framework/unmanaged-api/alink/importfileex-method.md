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
ms.workload: dotnet
ms.openlocfilehash: dc2af9db27c5194a1bdcef875b8db8d458d0edfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex-method"></a><span data-ttu-id="29eaf-102">ImportFileEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="29eaf-102">ImportFileEx Method</span></span>
<span data-ttu-id="29eaf-103">Importy wskazane zestawu lub modułu niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="29eaf-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29eaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29eaf-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="29eaf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29eaf-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="29eaf-106">Pełna nazwa pliku, z którego będą importowane.</span><span class="sxs-lookup"><span data-stu-id="29eaf-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="29eaf-107">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="29eaf-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="29eaf-108">Jeśli PRAWDA, ImportTypes jest używany, w przeciwnym razie importowanie musi zostać wykonana ręcznie.</span><span class="sxs-lookup"><span data-stu-id="29eaf-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="29eaf-109">Flagi są przekazywane do [OpenScope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="29eaf-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="29eaf-110">Odbiera identyfikator importowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="29eaf-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="29eaf-111">Odbiera zakresu importu zestawu [IMetaDataAssemblyImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="29eaf-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="29eaf-112">Jest ustawiony na wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="29eaf-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="29eaf-113">Odbiera liczba importowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="29eaf-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29eaf-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29eaf-114">Return Value</span></span>  
 <span data-ttu-id="29eaf-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="29eaf-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29eaf-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29eaf-116">Requirements</span></span>  
 <span data-ttu-id="29eaf-117">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="29eaf-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29eaf-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29eaf-118">See Also</span></span>  
 [<span data-ttu-id="29eaf-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="29eaf-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="29eaf-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="29eaf-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="29eaf-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="29eaf-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
