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
ms.openlocfilehash: b842f44711d38a996b9d710dbe8bd369d30c5443
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051887"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="19e87-102">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="19e87-102">Calling a DLL Function</span></span>
<span data-ttu-id="19e87-103">Chociaż wywoływanie niezarządzanych funkcji DLL jest niemal identyczne z wywoływaniem innego kodu zarządzanego, istnieją różnice, które mogą sprawiać, że funkcje DLL pozornie pomyleją się w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="19e87-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="19e87-104">W tej sekcji przedstawiono tematy opisujące niektóre nietypowe problemy związane z wywoływaniem.</span><span class="sxs-lookup"><span data-stu-id="19e87-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="19e87-105">Struktury zwracane przez wywołania wywołania platformy muszą być typami danych, które mają taką samą reprezentację w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="19e87-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="19e87-106">Typy takie są nazywane *danych kopiowalnych* , ponieważ nie wymagają konwersji (zobacz [typy danych kopiowalnych i danych kopiowalnych](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="19e87-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="19e87-107">Aby wywołać funkcję, która ma strukturę niedanych kopiowalnychną jako typ zwracany, można zdefiniować typ pomocnika danych kopiowalnych o takim samym rozmiarze co typ inny niż danych kopiowalnych i przekonwertować dane po powrocie funkcji.</span><span class="sxs-lookup"><span data-stu-id="19e87-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19e87-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="19e87-108">In This Section</span></span>  
 [<span data-ttu-id="19e87-109">Przekazywanie struktur</span><span class="sxs-lookup"><span data-stu-id="19e87-109">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="19e87-110">Identyfikuje problemy z przekazywaniem struktur danych ze wstępnie zdefiniowanym układem.</span><span class="sxs-lookup"><span data-stu-id="19e87-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="19e87-111">Funkcje wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="19e87-111">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="19e87-112">Zawiera podstawowe informacje na temat funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19e87-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="19e87-113">Instrukcje: Implementowanie funkcji wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="19e87-113">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="19e87-114">Opisuje sposób implementowania funkcji wywołania zwrotnego w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="19e87-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="19e87-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="19e87-115">Related Sections</span></span>  
 [<span data-ttu-id="19e87-116">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="19e87-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="19e87-117">Opisuje sposób wywoływania niezarządzanych funkcji DLL przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="19e87-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="19e87-118">Marshaling danych w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="19e87-118">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="19e87-119">Opisuje sposób deklarowania parametrów metody i przekazywania argumentów do funkcji wyeksportowanych przez niezarządzane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="19e87-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
