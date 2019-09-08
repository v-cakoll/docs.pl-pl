---
title: EmitAssemblyCustomAttribute — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77d54f6c8f67dda5132518d1fbd579a91ce82071
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777440"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="34d02-102">EmitAssemblyCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="34d02-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="34d02-103">Wywołanie ustawiania atrybutów niestandardowych na poziomie zestawu.</span><span class="sxs-lookup"><span data-stu-id="34d02-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34d02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="34d02-104">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="34d02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34d02-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="34d02-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="34d02-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="34d02-107">Plik, który deplikuje atrybut.</span><span class="sxs-lookup"><span data-stu-id="34d02-107">File that defiles the attribute.</span></span> <span data-ttu-id="34d02-108">Może mieć wartość null `AssemblyID` , jeśli nie wskazuje niepowiązanego modułu.</span><span class="sxs-lookup"><span data-stu-id="34d02-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="34d02-109">Typ atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="34d02-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="34d02-110">Dane wartości niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="34d02-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="34d02-111">Długość danych wartości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="34d02-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="34d02-112">Ma wartość TRUE, jeśli atrybut niestandardowy jest powiązany z podpisywaniem zestawu.</span><span class="sxs-lookup"><span data-stu-id="34d02-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="34d02-113">Ma wartość TRUE, jeśli wiele atrybutów ma być emitowanych.</span><span class="sxs-lookup"><span data-stu-id="34d02-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34d02-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="34d02-114">Return Value</span></span>  
 <span data-ttu-id="34d02-115">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34d02-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34d02-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34d02-116">Requirements</span></span>  
 <span data-ttu-id="34d02-117">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="34d02-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d02-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34d02-118">See also</span></span>

- [<span data-ttu-id="34d02-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="34d02-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="34d02-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="34d02-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="34d02-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="34d02-121">ALink API</span></span>](index.md)
