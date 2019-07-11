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
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741536"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="0f54c-102">SetAssemblyFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f54c-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="0f54c-103">Przypisuje nazwę zestawu, który ma zostać utworzony.</span><span class="sxs-lookup"><span data-stu-id="0f54c-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="0f54c-104">Nie do wykorzystania podczas produkowania niepowiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="0f54c-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f54c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f54c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f54c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f54c-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="0f54c-107">W pełni kwalifikowana nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="0f54c-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="0f54c-108">Wskaźnik do [IMetaDataEmit — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0f54c-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="0f54c-109">Flagi zgodnie z definicją w [assemblyflags — wyliczenie](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0f54c-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="0f54c-110">Wskaźnik do Identyfikatora Wynikowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="0f54c-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f54c-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f54c-111">Return Value</span></span>  
 <span data-ttu-id="0f54c-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0f54c-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f54c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f54c-113">Requirements</span></span>  
 <span data-ttu-id="0f54c-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="0f54c-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f54c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f54c-115">See also</span></span>

- [<span data-ttu-id="0f54c-116">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f54c-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0f54c-117">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f54c-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0f54c-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="0f54c-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
