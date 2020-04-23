---
title: Tworzenie klasy utrzymującej funkcje DLL
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: 765d4344553a6e65b930a7bf586a41144d220fc6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123624"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="186ff-102">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="186ff-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="186ff-103">Otoka często używanej funkcji DLL w klasie zarządzanej jest skutecznym podejściem do hermetyzacji funkcjonalności platformy.</span><span class="sxs-lookup"><span data-stu-id="186ff-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="186ff-104">Chociaż nie jest to konieczne w każdym przypadku, zapewnienie otoki klasy jest wygodne, ponieważ Definiowanie funkcji DLL może być kłopotliwe i podatne na błędy.</span><span class="sxs-lookup"><span data-stu-id="186ff-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="186ff-105">W przypadku programowania w Visual Basic lub C# należy zadeklarować funkcje DLL w ramach klasy lub modułu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="186ff-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="186ff-106">W obrębie klasy należy zdefiniować metodę statyczną dla każdej funkcji DLL, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="186ff-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="186ff-107">Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub Konwencja wywoływania używana w argumentach metod przekazywania; Pomijając te informacje, należy wybrać ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="186ff-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="186ff-108">Aby zapoznać się z pełną listą opcji deklaracji i ich ustawień domyślnych, zobacz [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="186ff-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="186ff-109">Po zapakowaniu można wywołać metody klasy podczas wywoływania metod statycznych dla każdej innej klasy.</span><span class="sxs-lookup"><span data-stu-id="186ff-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="186ff-110">Funkcja Invoke platformy obsługuje automatycznie wyeksportowaną funkcję.</span><span class="sxs-lookup"><span data-stu-id="186ff-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="186ff-111">Podczas projektowania zarządzanej klasy dla wywołania platformy należy wziąć pod uwagę relacje między klasami i funkcjami DLL.</span><span class="sxs-lookup"><span data-stu-id="186ff-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="186ff-112">Można na przykład:</span><span class="sxs-lookup"><span data-stu-id="186ff-112">For example, you can:</span></span>  
  
- <span data-ttu-id="186ff-113">Deklarowanie funkcji DLL w obrębie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="186ff-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="186ff-114">Utwórz pojedynczą klasę dla każdej funkcji DLL, utrzymując funkcje izolowane i łatwe do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="186ff-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="186ff-115">Utwórz jedną klasę dla zestawu powiązanych funkcji DLL, aby tworzyć logiczne grupowania i zmniejszać obciążenie.</span><span class="sxs-lookup"><span data-stu-id="186ff-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="186ff-116">W tym celu można nazwać klasę i jej metody.</span><span class="sxs-lookup"><span data-stu-id="186ff-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="186ff-117">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="186ff-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186ff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="186ff-118">See also</span></span>

- [<span data-ttu-id="186ff-119">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="186ff-119">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="186ff-120">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="186ff-120">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="186ff-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="186ff-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="186ff-122">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="186ff-122">Calling a DLL Function</span></span>](calling-a-dll-function.md)
