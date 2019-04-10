---
title: Wymagane odwołanie do zestawu „<assemblyidentity>” z typem „<typename>”, ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami „<projectname1>” i „<projectname2>”.
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 9868598b32ae17ef5bfb5dd738f8a7541515f5ec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310674"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="2c6e2-102">Wymagane odwołanie do zestawu "\<assemblyidentity >" z typem "\<typename >", ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami\<projectname1 > "i"\< projectname2 > "</span><span class="sxs-lookup"><span data-stu-id="2c6e2-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="2c6e2-103">Wyrażenia o typie, takich jak klasy, struktury, interfejsu, wyliczenie lub delegata, który jest zdefiniowany poza projektem.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="2c6e2-104">Jednak masz odwołania do więcej niż jeden zestaw definiujący ten typ projektu.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="2c6e2-105">Projekty wspominane produkują zestawy o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="2c6e2-106">W związku z tym kompilator nie może określić uzyskują dostęp do których zestawu do użycia dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="2c6e2-107">Aby uzyskać dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołania do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="2c6e2-108">Musi to być odwołanie pojedynczego, jednoznaczną nie powoduje odwołania cykliczne między projektami.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="2c6e2-109">**Identyfikator błędu:** BC30969</span><span class="sxs-lookup"><span data-stu-id="2c6e2-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c6e2-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2c6e2-110">To correct this error</span></span>  
  
1. <span data-ttu-id="2c6e2-111">Ustal, który projekt daje najlepsze zestawu dla Twojego projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="2c6e2-112">Ta decyzja można skorzystać z kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="2c6e2-113">We właściwościach projektu Dodaj odwołanie do pliku, który zawiera zestaw, który definiuje typ, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="2c6e2-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c6e2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c6e2-114">See also</span></span>

- [<span data-ttu-id="2c6e2-115">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="2c6e2-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="2c6e2-116">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="2c6e2-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="2c6e2-117">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="2c6e2-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2c6e2-118">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="2c6e2-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
