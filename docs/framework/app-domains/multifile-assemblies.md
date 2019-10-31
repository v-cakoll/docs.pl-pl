---
title: Zestawy wieloplikowe
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
ms.openlocfilehash: 8ffb0482ebd01a056d9ffd80a74ec0332e1b8dff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119793"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="b0ef8-102">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="b0ef8-102">Multifile assemblies</span></span>

<span data-ttu-id="b0ef8-103">Można tworzyć zestawy wieloplikowe przeznaczone dla .NET Framework przy użyciu kompilatorów wiersza polecenia lub programu Visual Studio z wizualizacją C++.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-103">You can create multifile assemblies that target the .NET Framework using command-line compilers or Visual Studio with Visual C++.</span></span> <span data-ttu-id="b0ef8-104">Jeden plik w zestawie musi zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="b0ef8-105">Zestaw, który uruchamia aplikację, musi również zawierać punkt wejścia, taki jak `Main` lub `WinMain`.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-105">An assembly that starts an application must also contain an entry point, such as a `Main` or `WinMain` method.</span></span>

<span data-ttu-id="b0ef8-106">Załóżmy na przykład, że masz aplikację, która zawiera dwa moduły kodu, *Client.cs* i *Stringer.cs*.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-106">For example, suppose you have an application that contains two code modules, *Client.cs* and *Stringer.cs*.</span></span> <span data-ttu-id="b0ef8-107">*Stringer.cs* tworzy przestrzeń nazw `myStringer`, do której odwołuje się kod w *Client.cs*.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-107">*Stringer.cs* creates the `myStringer` namespace that is referenced by the code in *Client.cs*.</span></span> <span data-ttu-id="b0ef8-108">*Client.cs* zawiera metodę `Main`, która jest punktem wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-108">*Client.cs* contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="b0ef8-109">W tym przykładzie kompilujesz dwa moduły kodu, a następnie utworzysz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="b0ef8-110">Manifest zestawu odwołuje się zarówno do modułów *klienta* , jak i *Stringer* .</span><span class="sxs-lookup"><span data-stu-id="b0ef8-110">The assembly manifest references both the *Client* and *Stringer* modules.</span></span>

> [!NOTE]
> <span data-ttu-id="b0ef8-111">Zestawy wieloplikowe mogą mieć tylko jeden punkt wejścia, nawet jeśli zestaw ma wiele modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>

<span data-ttu-id="b0ef8-112">Istnieje kilka powodów, dla których warto utworzyć zestaw wieloplikowy:</span><span class="sxs-lookup"><span data-stu-id="b0ef8-112">There are several reasons you might want to create a multifile assembly:</span></span>

- <span data-ttu-id="b0ef8-113">Do łączenia modułów pisanych w różnych językach.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-113">To combine modules written in different languages.</span></span> <span data-ttu-id="b0ef8-114">Jest to najbardziej typowy powód tworzenia zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-114">This is the most common reason for creating a multifile assembly.</span></span>

- <span data-ttu-id="b0ef8-115">Aby zoptymalizować pobieranie aplikacji przez umieszczenie rzadko używanych typów w module, który jest pobierany tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b0ef8-116">Jeśli tworzysz aplikacje, które zostaną pobrane przy użyciu znacznika `<object>` w programie Microsoft Internet Explorer, ważne jest, aby utworzyć zestawy wieloplikowe.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="b0ef8-117">W tym scenariuszu utworzysz plik oddzielony od modułów kodu, który zawiera tylko manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="b0ef8-118">Program Internet Explorer najpierw pobierze manifest zestawu, a następnie utworzy wątki robocze do pobrania wymaganych modułów lub zestawów.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="b0ef8-119">Podczas pobierania pliku zawierającego manifest zestawu program Internet Explorer nie będzie odpowiadać na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="b0ef8-120">Im mniejszy plik zawierający manifest zestawu, tym mniej czasu program Internet Explorer nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>

- <span data-ttu-id="b0ef8-121">Do łączenia modułów kodu pisanych przez kilku deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="b0ef8-122">Chociaż każdy deweloper może kompilować każdy moduł kodu do zestawu, może to spowodować, że niektóre typy mają być ujawnione publicznie, które nie są ujawniane, jeśli wszystkie moduły są umieszczane w zestawie wieloplikowym.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>

<span data-ttu-id="b0ef8-123">Po utworzeniu zestawu można podpisać plik, który zawiera manifest zestawu, a tym samym zestaw lub można nadać plikowi i zestawowi silną nazwę i umieścić go w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b0ef8-123">Once you create the assembly, you can sign the file that contains the assembly manifest, and hence the assembly, or you can give the file and the assembly a strong name and put it in the global assembly cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0ef8-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0ef8-124">See also</span></span>

- [<span data-ttu-id="b0ef8-125">Instrukcje: kompilowanie zestawu wieloplikowego</span><span class="sxs-lookup"><span data-stu-id="b0ef8-125">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="b0ef8-126">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="b0ef8-126">Program with assemblies</span></span>](../../standard/assembly/program.md)
