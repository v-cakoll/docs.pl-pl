---
title: SetAssemblyFile2 — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d96881ce35dca1ee7a196507ef8d81a565eed82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741501"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="08e50-102">SetAssemblyFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="08e50-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="08e50-103">Określa nazwę i opcje dla nowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="08e50-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="08e50-104">Ta metoda zostanie wywołana podczas tworzenia modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="08e50-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e50-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="08e50-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="08e50-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="08e50-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="08e50-107">Nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="08e50-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="08e50-108">[Imetadataemit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejsu dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="08e50-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="08e50-109">Opcje reprezentowany przez [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="08e50-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="08e50-110">Otrzymuje unikatowy identyfikator dla zestawu podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="08e50-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08e50-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="08e50-111">Return Value</span></span>  
 <span data-ttu-id="08e50-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="08e50-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08e50-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="08e50-113">Requirements</span></span>  
 <span data-ttu-id="08e50-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="08e50-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e50-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08e50-115">See also</span></span>

- [<span data-ttu-id="08e50-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="08e50-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="08e50-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="08e50-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="08e50-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="08e50-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
