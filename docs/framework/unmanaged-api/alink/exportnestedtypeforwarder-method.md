---
title: ExportNestedTypeForwarder — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedTypeForwarder
helpviewer_keywords:
- ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type:
- apiref
ms.openlocfilehash: cc81ccd1c754e3d34c54737f4560b4f81d5cc916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438412"
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="8ed16-102">ExportNestedTypeForwarder — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ed16-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="8ed16-103">Dodaje funkcję przesyłania dalej typu dla typu zagnieżdżonego do tabeli typów danego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8ed16-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ed16-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ed16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ed16-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8ed16-106">Identyfikator zestawu do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="8ed16-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8ed16-107">Token pliku lub identyfikator zestawu, który definiuje typ.</span><span class="sxs-lookup"><span data-stu-id="8ed16-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="8ed16-108">Token dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="8ed16-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="8ed16-109">Token typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8ed16-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="8ed16-110">W pełni kwalifikowana nazwa typu do eksportowania.</span><span class="sxs-lookup"><span data-stu-id="8ed16-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8ed16-111">`ComType` flagi, takie jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="8ed16-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="8ed16-112">Odbiera token typu eksportu.</span><span class="sxs-lookup"><span data-stu-id="8ed16-112">Receives token of export type.</span></span> <span data-ttu-id="8ed16-113">Jest to konieczne tylko w przypadku emitowania typów zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="8ed16-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ed16-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ed16-114">Return Value</span></span>  
 <span data-ttu-id="8ed16-115">Zwraca S_OK, jeśli metoda zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ed16-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed16-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ed16-116">Requirements</span></span>  
 <span data-ttu-id="8ed16-117">Wymaga Alink. h</span><span class="sxs-lookup"><span data-stu-id="8ed16-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed16-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ed16-118">See also</span></span>

- [<span data-ttu-id="8ed16-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ed16-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8ed16-120">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ed16-120">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8ed16-121">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="8ed16-121">ALink API</span></span>](index.md)
