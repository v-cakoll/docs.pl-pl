---
title: ImportTypes — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 321038a148c27086ca499e2f448eb50cb93525ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405515"
---
# <a name="importtypes-method"></a><span data-ttu-id="e0a68-102">ImportTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0a68-102">ImportTypes Method</span></span>
<span data-ttu-id="e0a68-103">Inicjuje importowanie typów z każdym zakresem importować za pomocą [ImportFile — metoda](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="e0a68-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0a68-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0a68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a68-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e0a68-106">Identyfikator zestawu, aby zaimportować.</span><span class="sxs-lookup"><span data-stu-id="e0a68-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e0a68-107">Identyfikator pliku importowanego.</span><span class="sxs-lookup"><span data-stu-id="e0a68-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="e0a68-108">Liczony od zera zakres do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="e0a68-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="e0a68-109">Odbiera uchwytu modułu wyliczającego dla typów w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e0a68-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="e0a68-110">Opcjonalnie odbiera [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e0a68-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="e0a68-111">Opcjonalnie odbiera liczba typów w zakresie wskazane.</span><span class="sxs-lookup"><span data-stu-id="e0a68-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a68-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0a68-112">Return Value</span></span>  
 <span data-ttu-id="e0a68-113">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e0a68-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a68-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0a68-114">Requirements</span></span>  
 <span data-ttu-id="e0a68-115">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="e0a68-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a68-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0a68-116">See Also</span></span>  
 [<span data-ttu-id="e0a68-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a68-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e0a68-118">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a68-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e0a68-119">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="e0a68-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
