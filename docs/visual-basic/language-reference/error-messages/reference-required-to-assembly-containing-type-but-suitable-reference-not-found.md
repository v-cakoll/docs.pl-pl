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
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="66fc1-102">Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt;&#39; zawierający typ &#39;&lt; Właściwość TypeName&gt;&#39; ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami &#39;&lt; projectname1&gt;&#39; i &#39;&lt; projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="66fc1-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="66fc1-103">Wyrażenie korzysta z typu, takich jak klasy, struktury, interfejsu, wyliczenie lub delegata, który jest zdefiniowany poza projektem.</span><span class="sxs-lookup"><span data-stu-id="66fc1-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="66fc1-104">Jednak masz odwołań do więcej niż jeden zestaw definiujący ten typ projektu.</span><span class="sxs-lookup"><span data-stu-id="66fc1-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="66fc1-105">Projekty cytowane utworzyć zestawów o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="66fc1-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="66fc1-106">W związku z tym kompilator nie może określić uzyskują dostęp do zestawu, które do użycia dla typu.</span><span class="sxs-lookup"><span data-stu-id="66fc1-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="66fc1-107">Dostęp do typu zdefiniowanego w innym zestawie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora musi mieć odwołanie do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="66fc1-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="66fc1-108">Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.</span><span class="sxs-lookup"><span data-stu-id="66fc1-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="66fc1-109">**Identyfikator błędu:** BC30969</span><span class="sxs-lookup"><span data-stu-id="66fc1-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66fc1-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="66fc1-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="66fc1-111">Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="66fc1-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="66fc1-112">Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="66fc1-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="66fc1-113">We właściwościach projektu Dodaj odwołanie do pliku, który zawiera zestaw, który definiuje typ, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="66fc1-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fc1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66fc1-114">See Also</span></span>  
 [<span data-ttu-id="66fc1-115">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="66fc1-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="66fc1-116">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="66fc1-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="66fc1-117">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="66fc1-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="66fc1-118">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="66fc1-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
