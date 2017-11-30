---
title: "&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39;&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a30e5d5aca09e7b74e16dd05cdc0c5c361c1657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="316e8-102">&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39;&lt; AssemblyName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="316e8-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="316e8-103">\<komunikat > tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu "\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="316e8-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="316e8-104">W takim przypadku spróbuj zamienić odwołanie pliku do "\<assemblyfilename >" w projekcie "\<projectname1 >" na odwołanie projektu do "\<projectname2 >".</span><span class="sxs-lookup"><span data-stu-id="316e8-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="316e8-105">Członkiem innego projektu uzyskuje dostęp do kodu w projekcie, ale nie zezwala na konfigurację rozwiązania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora rozpoznać odwołania.</span><span class="sxs-lookup"><span data-stu-id="316e8-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="316e8-106">Dostęp do typu zdefiniowanego w innym zestawie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora musi mieć odwołanie do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="316e8-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="316e8-107">Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.</span><span class="sxs-lookup"><span data-stu-id="316e8-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="316e8-108">**Identyfikator błędu:** BC30971</span><span class="sxs-lookup"><span data-stu-id="316e8-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="316e8-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="316e8-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="316e8-110">Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="316e8-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="316e8-111">Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="316e8-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="316e8-112">We właściwościach projektu Dodaj odwołanie do projektu, który zawiera zestaw, który definiuje typ, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="316e8-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316e8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="316e8-113">See Also</span></span>  
 [<span data-ttu-id="316e8-114">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="316e8-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="316e8-115">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="316e8-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="316e8-116">NIB porady: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="316e8-116">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="316e8-117">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="316e8-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="316e8-118">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="316e8-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
