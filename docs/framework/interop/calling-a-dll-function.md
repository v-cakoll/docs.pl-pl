---
title: Wywołanie funkcji DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643572"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="587a9-102">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="587a9-102">Calling a DLL Function</span></span>
<span data-ttu-id="587a9-103">Wywoływanie niezarządzanych funkcji DLL jest niemal identyczne do wywoływania innego kodu zarządzanego, istnieją różnice, które mogą ułatwić funkcji DLL wydawać się niejasne na początku.</span><span class="sxs-lookup"><span data-stu-id="587a9-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="587a9-104">Ta sekcja wprowadza tematach opisano niektóre nietypowe problemy związane z wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="587a9-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="587a9-105">Wywołania struktury, które są zwracane z platformy musi być typy danych, które mają tę samą reprezentację w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="587a9-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="587a9-106">Typy takie są nazywane *kopiowalnymi* , ponieważ nie wymaga konwersji (zobacz [Kopiowalne i typy danych Kopiowalnych inne niż](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="587a9-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="587a9-107">Aby wywołać funkcję, która ma strukturę niekopiowalnych jako jego typem zwracanym, może definiowaniu typu Pomocnika danych kopiowalnych taki sam rozmiar jak typ niekopiowalnych i konwersji danych, po powrocie funkcji.</span><span class="sxs-lookup"><span data-stu-id="587a9-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="587a9-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="587a9-108">In This Section</span></span>  
 [<span data-ttu-id="587a9-109">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="587a9-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="587a9-110">Identyfikuje problemy dotyczące przekazywania struktur danych przy użyciu wstępnie zdefiniowanego układu.</span><span class="sxs-lookup"><span data-stu-id="587a9-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="587a9-111">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="587a9-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="587a9-112">Zawiera podstawowe informacje o funkcjach wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="587a9-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="587a9-113">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="587a9-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="587a9-114">Opisuje sposób implementacji funkcji wywołania zwrotnego w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="587a9-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="587a9-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="587a9-115">Related Sections</span></span>  
 [<span data-ttu-id="587a9-116">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="587a9-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="587a9-117">W tym artykule opisano sposób wywoływania niezarządzanego wywoływanie funkcji DLL za pomocą platformy.</span><span class="sxs-lookup"><span data-stu-id="587a9-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="587a9-118">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="587a9-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="587a9-119">W tym artykule opisano, jak deklarować parametrów metod i przekazywać argumenty do funkcji eksportowanych przez niezarządzanych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="587a9-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
