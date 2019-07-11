---
title: ImportFileEx — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcf714cb0c1c1dd59ae2ec56279870c0bb3e1c4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741720"
---
# <a name="importfileex-method"></a><span data-ttu-id="7a829-102">ImportFileEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a829-102">ImportFileEx Method</span></span>
<span data-ttu-id="7a829-103">Importy wykazały, zestaw lub moduł niepowiązanej.</span><span class="sxs-lookup"><span data-stu-id="7a829-103">Imports indicated assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a829-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a829-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7a829-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a829-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="7a829-106">W pełni kwalifikowana nazwa pliku, z którego chcesz zaimportować.</span><span class="sxs-lookup"><span data-stu-id="7a829-106">Fully qualified name of file from which to import.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="7a829-107">Opcjonalna nazwa pliku docelowego.</span><span class="sxs-lookup"><span data-stu-id="7a829-107">Optional name of target file.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="7a829-108">W przypadku opcji TRUE importtypes — jest używana, w przeciwnym razie importowanie muszą być wykonywane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="7a829-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7a829-109">Flagi, aby być przekazywane do [openscope — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span><span class="sxs-lookup"><span data-stu-id="7a829-109">Flags to be passed along to [OpenScope Method](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="7a829-110">Odbiera identyfikator pliku zostały zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="7a829-110">Receives ID of the file being imported.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="7a829-111">Odbiera zakresu importu zestawu [imetadataassemblyimport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7a829-111">Receives assembly import scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="7a829-112">Jest ustawiona na wartość NULL, jeśli plik nie jest zestawem.</span><span class="sxs-lookup"><span data-stu-id="7a829-112">Is set to NULL if file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="7a829-113">Odbiera liczbę zaimportowanych plików i/lub zakresów.</span><span class="sxs-lookup"><span data-stu-id="7a829-113">Receives count of imported files and/or scopes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a829-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7a829-114">Return Value</span></span>  
 <span data-ttu-id="7a829-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7a829-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a829-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a829-116">Requirements</span></span>  
 <span data-ttu-id="7a829-117">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="7a829-117">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a829-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a829-118">See also</span></span>

- [<span data-ttu-id="7a829-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a829-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="7a829-120">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a829-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="7a829-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="7a829-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
