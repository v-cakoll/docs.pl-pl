---
title: Zestawy wieloplikowe
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bad63bbc8e221f306e5807f51fbbb8eb4761d0fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705483"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="854f8-102">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="854f8-102">Multifile Assemblies</span></span>

<span data-ttu-id="854f8-103">Można utworzyć zestawy wieloplikowe, za pomocą kompilatorów wiersza polecenia lub programu Visual Studio z programem Visual C++.</span><span class="sxs-lookup"><span data-stu-id="854f8-103">You can create multifile assemblies using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="854f8-104">Jeden plik w zestawie musi zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="854f8-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="854f8-105">Zestaw, który uruchamia aplikację musi również zawierać punkt wejścia, takich jak metoda Main lub WinMain.</span><span class="sxs-lookup"><span data-stu-id="854f8-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>

<span data-ttu-id="854f8-106">Na przykład załóżmy, że gdy masz już aplikację, która zawiera dwa moduły kodu Client.cs i Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="854f8-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="854f8-107">Tworzy Stringer.cs `myStringer` przestrzeni nazw, która odwołuje się kod w Client.cs.</span><span class="sxs-lookup"><span data-stu-id="854f8-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="854f8-108">Zawiera Client.cs `Main` metoda, która jest punkt wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="854f8-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="854f8-109">W tym przykładzie skompilować modułów kodu dwa, a następnie utwórz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="854f8-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="854f8-110">Manifest zestawu odwołuje się do zarówno `Client` i `Stringer` modułów.</span><span class="sxs-lookup"><span data-stu-id="854f8-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>

> [!NOTE]
> <span data-ttu-id="854f8-111">Zestawy wieloplikowe może mieć tylko jeden wpis punktu, nawet jeśli zestaw ma wiele modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="854f8-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="854f8-112">Istnieje kilka powodów, warto utworzyć zestaw wieloplikowy:</span><span class="sxs-lookup"><span data-stu-id="854f8-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="854f8-113">Aby połączyć modułów napisanych w różnych językach.</span><span class="sxs-lookup"><span data-stu-id="854f8-113">To combine modules written in different languages.</span></span> <span data-ttu-id="854f8-114">Jest to najbardziej typowe przyczyny tworzenia zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="854f8-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="854f8-115">Aby zoptymalizować, pobierania aplikacji poprzez umieszczenie rzadko używanych typów w module, który jest pobierany tylko wtedy, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="854f8-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="854f8-116">Jeśli tworzysz aplikacje, które będą pobierane przy użyciu `<object>` tagu za pomocą programu Microsoft Internet Explorer jest ważne, aby utworzyć zestawy wieloplikowe.</span><span class="sxs-lookup"><span data-stu-id="854f8-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="854f8-117">W tym scenariuszu utworzysz plik oddzielnie od moduły kodu, które zawiera jedynie manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="854f8-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="854f8-118">Program Internet Explorer pliki do pobrania manifestu zestawu, a następnie tworzy wątków do pobierania dodatkowych modułów ani zestawów wymaganych.</span><span class="sxs-lookup"><span data-stu-id="854f8-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="854f8-119">Podczas pobierania pliku zawierającego manifest zestawu Internet Explorer będzie odpowiadać na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="854f8-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="854f8-120">Mniejszy plik zawierający manifest zestawu, tym krótszy czas programu Internet Explorer będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="854f8-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="854f8-121">Aby połączyć modułów kodu, napisanych przez wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="854f8-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="854f8-122">Mimo że każdy deweloper może skompilować poszczególnych modułów kodu do zestawu, to wymuszenie pewnych typów publicznie narażonych, które nie są widoczne, jeśli wszystkie moduły są umieszczane w zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="854f8-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="854f8-123">Po utworzeniu zestawu, możesz utworzyć plik, który zawiera manifest zestawu (i tym samym zestawie), lub możesz nadać silnej nazwy pliku (i zestawu) i umieścić go w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="854f8-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="854f8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="854f8-124">See also</span></span>

- [<span data-ttu-id="854f8-125">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="854f8-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="854f8-126">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="854f8-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)