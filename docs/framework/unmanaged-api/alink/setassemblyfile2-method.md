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
ms.openlocfilehash: 59bfc6785d3ad195e219afc323b7fdb513d8fefc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092568"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="49ee4-102">SetAssemblyFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="49ee4-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="49ee4-103">Określa nazwę i opcje dla nowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="49ee4-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="49ee4-104">Ta metoda zostanie wywołana podczas tworzenia modułów niepowiązanych.</span><span class="sxs-lookup"><span data-stu-id="49ee4-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49ee4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="49ee4-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="49ee4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="49ee4-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="49ee4-107">Nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="49ee4-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="49ee4-108">[Imetadataemit2 — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interfejsu dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="49ee4-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="49ee4-109">Opcje reprezentowany przez [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="49ee4-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="49ee4-110">Otrzymuje unikatowy identyfikator dla zestawu podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="49ee4-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49ee4-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49ee4-111">Return Value</span></span>  
 <span data-ttu-id="49ee4-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="49ee4-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49ee4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49ee4-113">Requirements</span></span>  
 <span data-ttu-id="49ee4-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="49ee4-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ee4-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49ee4-115">See also</span></span>

- [<span data-ttu-id="49ee4-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="49ee4-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="49ee4-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="49ee4-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="49ee4-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="49ee4-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
