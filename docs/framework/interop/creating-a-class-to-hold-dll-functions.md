---
title: Tworzenie klasy utrzymującej funkcje DLL
description: Utwórz otokę zarządzanej klasy w programie .NET, aby przechowywać funkcje DLL, które ułatwiają hermetyzację funkcjonalności platformy.
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
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622175"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="2f7c5-103">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="2f7c5-103">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="2f7c5-104">Otoka często używanej funkcji DLL w klasie zarządzanej jest skutecznym podejściem do hermetyzacji funkcjonalności platformy.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="2f7c5-105">Chociaż nie jest to konieczne w każdym przypadku, zapewnienie otoki klasy jest wygodne, ponieważ Definiowanie funkcji DLL może być kłopotliwe i podatne na błędy.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="2f7c5-106">W przypadku programowania w Visual Basic lub C# należy zadeklarować funkcje DLL w ramach klasy lub modułu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="2f7c5-107">W obrębie klasy należy zdefiniować metodę statyczną dla każdej funkcji DLL, która ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="2f7c5-108">Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub Konwencja wywoływania używana w argumentach metod przekazywania; Pomijając te informacje, należy wybrać ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="2f7c5-109">Aby zapoznać się z pełną listą opcji deklaracji i ich ustawień domyślnych, zobacz [Tworzenie prototypów w kodzie zarządzanym](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="2f7c5-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="2f7c5-110">Po zapakowaniu można wywołać metody klasy podczas wywoływania metod statycznych dla każdej innej klasy.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="2f7c5-111">Funkcja Invoke platformy obsługuje automatycznie wyeksportowaną funkcję.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="2f7c5-112">Podczas projektowania zarządzanej klasy dla wywołania platformy należy wziąć pod uwagę relacje między klasami i funkcjami DLL.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="2f7c5-113">Możesz na przykład:</span><span class="sxs-lookup"><span data-stu-id="2f7c5-113">For example, you can:</span></span>  
  
- <span data-ttu-id="2f7c5-114">Deklarowanie funkcji DLL w obrębie istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="2f7c5-115">Utwórz pojedynczą klasę dla każdej funkcji DLL, utrzymując funkcje izolowane i łatwe do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="2f7c5-116">Utwórz jedną klasę dla zestawu powiązanych funkcji DLL, aby tworzyć logiczne grupowania i zmniejszać obciążenie.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="2f7c5-117">W tym celu można nazwać klasę i jej metody.</span><span class="sxs-lookup"><span data-stu-id="2f7c5-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="2f7c5-118">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="2f7c5-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7c5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f7c5-119">See also</span></span>

- [<span data-ttu-id="2f7c5-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="2f7c5-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="2f7c5-121">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="2f7c5-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="2f7c5-122">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="2f7c5-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="2f7c5-123">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="2f7c5-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
