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
ms.openlocfilehash: 8612e8d598e7f92cd9fc0106f99d21a239db90b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742513"
---
# <a name="multifile-assemblies"></a><span data-ttu-id="302ac-102">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="302ac-102">Multifile Assemblies</span></span>
<span data-ttu-id="302ac-103">Możesz utworzyć wiele plików zestawów przy użyciu kompilatory w wierszu polecenia lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] z programem Visual C++.</span><span class="sxs-lookup"><span data-stu-id="302ac-103">You can create multifile assemblies using command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] with Visual C++.</span></span> <span data-ttu-id="302ac-104">Jeden plik w zestawie musi zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="302ac-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="302ac-105">Zestaw, który uruchamia aplikację musi również zawierać punkt wejścia, takich jak metoda Main lub WinMain.</span><span class="sxs-lookup"><span data-stu-id="302ac-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>  
  
 <span data-ttu-id="302ac-106">Na przykład załóżmy, że masz aplikację, która zawiera dwa moduły kodu, Client.cs i Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="302ac-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="302ac-107">Tworzy Stringer.cs `myStringer` przestrzeni nazw, która odwołuje się do niego kod w Client.cs.</span><span class="sxs-lookup"><span data-stu-id="302ac-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="302ac-108">Zawiera Client.cs `Main` metodę, która jest punkt wejścia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="302ac-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="302ac-109">W tym przykładzie skompilować modułów dwóch kodu, a następnie utwórz trzeci plik, który zawiera manifest zestawu, który uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="302ac-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="302ac-110">Manifest zestawu odwołuje się do obu `Client` i `Stringer` modułów.</span><span class="sxs-lookup"><span data-stu-id="302ac-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="302ac-111">Zestawy wieloplikowe może mieć tylko jeden wpis punktu, nawet jeśli zestaw ma wiele modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="302ac-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>  
  
 <span data-ttu-id="302ac-112">Istnieje kilka przyczyn, które można utworzyć zestawu wieloplikowego:</span><span class="sxs-lookup"><span data-stu-id="302ac-112">There are several reasons you might want to create a multifile assembly:</span></span>  
  
-   <span data-ttu-id="302ac-113">Aby połączyć modułów napisane w różnych językach.</span><span class="sxs-lookup"><span data-stu-id="302ac-113">To combine modules written in different languages.</span></span> <span data-ttu-id="302ac-114">Jest to najbardziej typowe przyczyny utworzenia zestawu wieloplikowego.</span><span class="sxs-lookup"><span data-stu-id="302ac-114">This is the most common reason for creating a multifile assembly.</span></span>  
  
-   <span data-ttu-id="302ac-115">Aby zoptymalizować pobieranie aplikacji przez umieszczenie rzadko używane typy w module, który jest pobierany tylko wtedy, gdy potrzebne.</span><span class="sxs-lookup"><span data-stu-id="302ac-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="302ac-116">Jeśli tworzysz aplikacje, które zostaną pobrane przy użyciu `<object>` tagu z programem Microsoft Internet Explorer jest ważne, aby utworzyć zestawy wieloplikowe.</span><span class="sxs-lookup"><span data-stu-id="302ac-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="302ac-117">W tym scenariuszu utworzysz plik oddzielony od własnych modułów kodu, które zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="302ac-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="302ac-118">Program Internet Explorer pliki do pobrania manifest zestawu, a następnie tworzy wątków roboczych, aby pobrać wszystkie dodatkowe moduły lub zestawy wymagane.</span><span class="sxs-lookup"><span data-stu-id="302ac-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="302ac-119">Podczas pobierania pliku manifestu zestawu zawierającego, program Internet Explorer będzie odpowiadać na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="302ac-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="302ac-120">Mniejsze pliku manifestu zestawu zawierającego mniej czasu programu Internet Explorer będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="302ac-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>  
  
-   <span data-ttu-id="302ac-121">Aby połączyć utworzona przez deweloperów kilka modułów kodu.</span><span class="sxs-lookup"><span data-stu-id="302ac-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="302ac-122">Mimo że każdy deweloper może skompilować poszczególnych modułów kodu w zespół, to wymuszenie niektóre typy uwidocznienia publicznie, które nie są dostępne, jeśli wszystkie moduły są umieszczane w zestawów wieloplikowych.</span><span class="sxs-lookup"><span data-stu-id="302ac-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>  
  
 <span data-ttu-id="302ac-123">Po utworzeniu zestawu, możesz utworzyć plik, który zawiera manifest zestawu (a tym samym zestawie), lub możesz nadać silnej nazwy pliku (i zestawu) i umieścić go w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="302ac-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="302ac-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="302ac-124">See Also</span></span>  
 [<span data-ttu-id="302ac-125">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="302ac-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="302ac-126">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="302ac-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
