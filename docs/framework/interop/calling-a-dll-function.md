---
title: Wywołanie funkcji DLL
description: Przejrzyj problemy dotyczące wywoływania funkcji DLL, która może wydawać się myląca. Proces wywoływania funkcji różni się w zależności od tego, czy typem zwracanym jest danych kopiowalnych.
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 90f8f47148e652a9942a35be1564bed94c155216
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620901"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="30644-104">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="30644-104">Calling a DLL Function</span></span>
<span data-ttu-id="30644-105">Chociaż wywoływanie niezarządzanych funkcji DLL jest niemal identyczne z wywoływaniem innego kodu zarządzanego, istnieją różnice, które mogą sprawiać, że funkcje DLL pozornie pomyleją się w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="30644-105">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="30644-106">W tej sekcji przedstawiono tematy opisujące niektóre nietypowe problemy związane z wywoływaniem.</span><span class="sxs-lookup"><span data-stu-id="30644-106">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="30644-107">Struktury zwracane przez wywołania wywołania platformy muszą być typami danych, które mają taką samą reprezentację w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="30644-107">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="30644-108">Typy takie są nazywane *danych kopiowalnych* , ponieważ nie wymagają konwersji (zobacz [typy danych kopiowalnych i danych kopiowalnych](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="30644-108">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="30644-109">Aby wywołać funkcję, która ma strukturę niedanych kopiowalnychną jako typ zwracany, można zdefiniować typ pomocnika danych kopiowalnych o takim samym rozmiarze co typ inny niż danych kopiowalnych i przekonwertować dane po powrocie funkcji.</span><span class="sxs-lookup"><span data-stu-id="30644-109">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30644-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="30644-110">In This Section</span></span>  
 [<span data-ttu-id="30644-111">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="30644-111">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="30644-112">Identyfikuje problemy z przekazywaniem struktur danych ze wstępnie zdefiniowanym układem.</span><span class="sxs-lookup"><span data-stu-id="30644-112">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="30644-113">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="30644-113">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="30644-114">Zawiera podstawowe informacje na temat funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="30644-114">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="30644-115">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="30644-115">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="30644-116">Opisuje sposób implementowania funkcji wywołania zwrotnego w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="30644-116">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30644-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="30644-117">Related Sections</span></span>  
 [<span data-ttu-id="30644-118">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="30644-118">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="30644-119">Opisuje sposób wywoływania niezarządzanych funkcji DLL przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="30644-119">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="30644-120">Organizowanie danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="30644-120">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="30644-121">Opisuje sposób deklarowania parametrów metody i przekazywania argumentów do funkcji wyeksportowanych przez niezarządzane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="30644-121">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
