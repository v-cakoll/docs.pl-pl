---
title: SetAssemblyFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a19762cbec91871d7af617957896e4ee34944fba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132718"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="93a33-102">SetAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="93a33-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="93a33-103">Przypisuje nazwę zestawu, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="93a33-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="93a33-104">Nie do wykorzystania podczas produkowania niepowiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="93a33-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a33-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a33-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="93a33-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="93a33-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="93a33-107">W pełni kwalifikowana nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="93a33-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="93a33-108">Wskaźnik do [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="93a33-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="93a33-109">Flagi zgodnie z definicją w [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="93a33-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="93a33-110">Wskaźnik do Identyfikatora Wynikowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="93a33-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93a33-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93a33-111">Return Value</span></span>  
 <span data-ttu-id="93a33-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="93a33-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a33-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93a33-113">Requirements</span></span>  
 <span data-ttu-id="93a33-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="93a33-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a33-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a33-115">See also</span></span>

- [<span data-ttu-id="93a33-116">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93a33-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="93a33-117">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93a33-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="93a33-118">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="93a33-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
