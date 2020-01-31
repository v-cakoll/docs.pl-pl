---
title: ISOSDacInterface, interfejs
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790481"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="ca752-102">ISOSDacInterface, interfejs</span><span class="sxs-lookup"><span data-stu-id="ca752-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="ca752-103">Zapewnia metody pomocnika do uzyskiwania dostępu do danych z `SOS`.</span><span class="sxs-lookup"><span data-stu-id="ca752-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="ca752-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca752-104">Methods</span></span>

| <span data-ttu-id="ca752-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca752-105">Method</span></span>                                                                                                               | <span data-ttu-id="ca752-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ca752-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ca752-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="ca752-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="ca752-108">Pobiera dane dla danego wskaźnika MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="ca752-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="ca752-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="ca752-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="ca752-110">Pobiera wskaźnik MethodDesc odpowiadającego metodzie zawierającej podanego adresu instrukcji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="ca752-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="ca752-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="ca752-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="ca752-112">Pobiera dane odpowiadające modułowi załadowanemu pod danym adresem.</span><span class="sxs-lookup"><span data-stu-id="ca752-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ca752-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca752-113">Remarks</span></span>

<span data-ttu-id="ca752-114">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ca752-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ca752-115">Jest to jednak interfejs COM, który pochodzi od `IUnknown` z identyfikatorem GUID `436f00f2-b42a-4b9f-870c-e73db66ae930`, który można uzyskać za pomocą zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="ca752-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ca752-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca752-116">Requirements</span></span>

<span data-ttu-id="ca752-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca752-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ca752-118">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ca752-118">**Header:** None</span></span>  
<span data-ttu-id="ca752-119">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ca752-119">**Library:** None</span></span>  
<span data-ttu-id="ca752-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ca752-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ca752-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca752-121">See also</span></span>

- [<span data-ttu-id="ca752-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ca752-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="ca752-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca752-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
