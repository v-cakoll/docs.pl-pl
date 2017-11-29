---
title: "Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt;&#39; zawierający typ &#39;&lt; Właściwość TypeName&gt;&#39; ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami &#39;&lt; projectname1&gt;&#39; i &#39;&lt; projectname2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="11c85-102">Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt;&#39; zawierający typ &#39;&lt; Właściwość TypeName&gt;&#39; ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami &#39;&lt; projectname1&gt;&#39; i &#39;&lt; projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="11c85-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="11c85-103">Wyrażenie korzysta z typu, takich jak klasy, struktury, interfejsu, wyliczenie lub delegata, który jest zdefiniowany poza projektem.</span><span class="sxs-lookup"><span data-stu-id="11c85-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="11c85-104">Jednak masz odwołań do więcej niż jeden zestaw definiujący ten typ projektu.</span><span class="sxs-lookup"><span data-stu-id="11c85-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="11c85-105">Projekty cytowane utworzyć zestawów o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="11c85-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="11c85-106">W związku z tym kompilator nie może określić uzyskują dostęp do zestawu, które do użycia dla typu.</span><span class="sxs-lookup"><span data-stu-id="11c85-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="11c85-107">Dostęp do typu zdefiniowanego w innym zestawie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora musi mieć odwołanie do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="11c85-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="11c85-108">Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.</span><span class="sxs-lookup"><span data-stu-id="11c85-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="11c85-109">**Identyfikator błędu:** BC30969</span><span class="sxs-lookup"><span data-stu-id="11c85-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11c85-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="11c85-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="11c85-111">Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="11c85-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="11c85-112">Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="11c85-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="11c85-113">We właściwościach projektu Dodaj odwołanie do pliku, który zawiera zestaw, który definiuje typ, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="11c85-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c85-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11c85-114">See Also</span></span>  
 [<span data-ttu-id="11c85-115">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="11c85-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="11c85-116">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="11c85-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="11c85-117">NIB porady: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="11c85-117">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="11c85-118">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="11c85-118">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="11c85-119">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="11c85-119">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
