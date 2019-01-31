---
title: Wymagane odwołanie do zestawu „<assemblyname>” z klasą bazową „<classname>”
ms.date: 07/20/2015
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
ms.openlocfilehash: 54848fdbd2547fe021f0386843f9666760396cb0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273283"
---
# <a name="reference-required-to-assembly-assemblyname-containing-the-base-class-classname"></a><span data-ttu-id="6bb68-102">Wymagane odwołanie do zestawu "\<nazwa_zestawu >" z klasą bazową\<nazwa_klasy > "</span><span class="sxs-lookup"><span data-stu-id="6bb68-102">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'</span></span>
<span data-ttu-id="6bb68-103">Wymagane odwołanie do zestawu "\<nazwa_zestawu >" z klasą bazową\<nazwa_klasy > ".</span><span class="sxs-lookup"><span data-stu-id="6bb68-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="6bb68-104">Dodaj je do projektu.</span><span class="sxs-lookup"><span data-stu-id="6bb68-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="6bb68-105">Klasa jest zdefiniowana w biblioteki dołączanej (dynamicznie DLL) lub zestawu, który nie jest bezpośrednio wywoływany w projekcie.</span><span class="sxs-lookup"><span data-stu-id="6bb68-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="6bb68-106">Kompilator Visual Basic wymaga odwołania, aby uniknąć niejednoznaczności, w przypadku, gdy klasa jest zdefiniowana w więcej niż jednego pliku DLL lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="6bb68-106">The Visual Basic compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="6bb68-107">**Identyfikator błędu:** BC30007</span><span class="sxs-lookup"><span data-stu-id="6bb68-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6bb68-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6bb68-108">To correct this error</span></span>  
  
-   <span data-ttu-id="6bb68-109">Obejmują nazwę bez odwołań biblioteki DLL lub zestawu w odwołaniach do projektu.</span><span class="sxs-lookup"><span data-stu-id="6bb68-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb68-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bb68-110">See also</span></span>

- [<span data-ttu-id="6bb68-111">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="6bb68-111">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="6bb68-112">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="6bb68-112">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
