---
title: "Wywołanie funkcji DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8755173b9c64a6457b94e689204c6a5aabc971cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="b1d4c-102">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b1d4c-102">Calling a DLL Function</span></span>
<span data-ttu-id="b1d4c-103">Wywoływanie niezarządzanych funkcji DLL jest niemal identyczny jak wywołanie innego kodu zarządzanego, istnieją różnice, które mogą ułatwić funkcji DLL wydaje się być mylące na początku.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="b1d4c-104">W tej sekcji przedstawiono tematach opisano niektóre z nietypowych problemów związanych z wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="b1d4c-105">Struktury, które są zwracane z platformy wywołania wywołania musi być typów danych, które mają taką samą reprezentację w kodzie zarządzane i niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="b1d4c-106">Takie typy są nazywane *typy kopiowalne* , ponieważ nie wymaga konwersji (zobacz [Kopiowalne i typy Kopiowalne inne niż](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="b1d4c-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="b1d4c-107">Aby wywołać funkcję, która ma strukturę niekopiowalne jako jej typu zwracanego, można zdefiniować typu pomocnika kopiowalne ten sam rozmiar jako typ niekopiowalne i Konwertuj dane po funkcja zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1d4c-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b1d4c-108">In This Section</span></span>  
 [<span data-ttu-id="b1d4c-109">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="b1d4c-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="b1d4c-110">Identyfikuje problemy przekazywanie struktur danych z układem wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="b1d4c-111">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="b1d4c-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="b1d4c-112">Zawiera podstawowe informacje o funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="b1d4c-113">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="b1d4c-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="b1d4c-114">Opisuje sposób Implementowanie funkcji wywołania zwrotnego w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b1d4c-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b1d4c-115">Related Sections</span></span>  
 [<span data-ttu-id="b1d4c-116">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b1d4c-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="b1d4c-117">Opisuje sposób wywoływania niezarządzanego wywołanie funkcji DLL przy użyciu platformy.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="b1d4c-118">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="b1d4c-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="b1d4c-119">Opisuje sposób deklarowanie parametrów metod i przekazywanie argumentów do funkcji wyeksportowane przez niezarządzanych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="b1d4c-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
