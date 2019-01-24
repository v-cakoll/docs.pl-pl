---
title: '&lt;komunikat&gt; tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: d4fb2a8985a21ecea5056b83d2766e8dc468180d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528995"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="d224a-102">&lt;komunikat&gt; tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="d224a-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="d224a-103">\<komunikat > tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu "\<nazwa_zestawu >.</span><span class="sxs-lookup"><span data-stu-id="d224a-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="d224a-104">W takim przypadku spróbuj wymienić odwołanie pliku do "\<assemblyfilename >' w projekcie"\<projectname1 > "z odwołaniem projektu do"\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="d224a-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="d224a-105">Kod w projekcie uzyskuje dostęp do składową innego projektu, ale konfiguracji rozwiązania nie zezwala na kompilator języka Visual Basic, aby rozpoznać odwołania.</span><span class="sxs-lookup"><span data-stu-id="d224a-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="d224a-106">Aby uzyskać dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołania do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d224a-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="d224a-107">Musi to być odwołanie pojedynczego, jednoznaczną nie powoduje odwołania cykliczne między projektami.</span><span class="sxs-lookup"><span data-stu-id="d224a-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="d224a-108">**Identyfikator błędu:** BC30971</span><span class="sxs-lookup"><span data-stu-id="d224a-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d224a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d224a-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="d224a-110">Ustal, który projekt daje najlepsze zestawu dla Twojego projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="d224a-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="d224a-111">Ta decyzja można skorzystać z kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="d224a-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="d224a-112">We właściwościach projektu Dodaj odwołanie do projektu, który zawiera zestaw, który definiuje typ, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="d224a-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d224a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d224a-113">See also</span></span>
- [<span data-ttu-id="d224a-114">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="d224a-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="d224a-115">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="d224a-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="d224a-116">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d224a-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="d224a-117">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="d224a-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
