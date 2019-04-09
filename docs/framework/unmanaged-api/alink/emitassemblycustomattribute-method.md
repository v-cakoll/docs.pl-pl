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
ms.openlocfilehash: 67073f04cfe981dd383369029d9a4b436929a0a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117848"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="84148-102">EmitAssemblyCustomAttribute — Metoda</span><span class="sxs-lookup"><span data-stu-id="84148-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="84148-103">Wywołać można ustawić na poziomie zestawu atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="84148-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84148-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84148-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="84148-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84148-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="84148-106">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="84148-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="84148-107">Plik, który defiles atrybutu.</span><span class="sxs-lookup"><span data-stu-id="84148-107">File that defiles the attribute.</span></span> <span data-ttu-id="84148-108">Może mieć wartości NULL, jeśli `AssemblyID` nie wskazuje niepowiązanych modułu netmodule.</span><span class="sxs-lookup"><span data-stu-id="84148-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="84148-109">Typ atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="84148-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="84148-110">Niestandardowa wartość danych.</span><span class="sxs-lookup"><span data-stu-id="84148-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="84148-111">Długość danych niestandardowych wartości.</span><span class="sxs-lookup"><span data-stu-id="84148-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="84148-112">Wartość TRUE, jeśli atrybut niestandardowy jest powiązany do podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="84148-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="84148-113">Wartość TRUE, jeśli wiele atrybutów, które mają być emitowane.</span><span class="sxs-lookup"><span data-stu-id="84148-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84148-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="84148-114">Return Value</span></span>  
 <span data-ttu-id="84148-115">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="84148-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84148-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84148-116">Requirements</span></span>  
 <span data-ttu-id="84148-117">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="84148-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84148-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84148-118">See also</span></span>

- [<span data-ttu-id="84148-119">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="84148-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="84148-120">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="84148-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="84148-121">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="84148-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
