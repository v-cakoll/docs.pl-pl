---
title: <message> Przyczyną tego błędu może być również połączenie odwołania pliku z odwołaniem projektu do zestawu „<assemblyname>"
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397262"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a><span data-ttu-id="74017-102">\<message> Przyczyną tego błędu może być również połączenie odwołania pliku z odwołaniem projektu do zestawu „\<assemblyname>"</span><span class="sxs-lookup"><span data-stu-id="74017-102">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>'</span></span>
<span data-ttu-id="74017-103">\<message>Ten błąd może również być spowodowany mieszaniem odwołania do pliku z odwołaniem projektu do zestawu " \<assemblyname> .</span><span class="sxs-lookup"><span data-stu-id="74017-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="74017-104">W takim przypadku Spróbuj zastąpić odwołanie do pliku " \<assemblyfilename> " w projekcie " \<projectname1> " z odwołaniem projektu do " \<projectname2> ".</span><span class="sxs-lookup"><span data-stu-id="74017-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="74017-105">Kod w projekcie uzyskuje dostęp do elementu członkowskiego innego projektu, ale Konfiguracja rozwiązania nie zezwala kompilatorowi Visual Basicemu na rozpoznanie odwołania.</span><span class="sxs-lookup"><span data-stu-id="74017-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="74017-106">Aby uzyskać dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołanie do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="74017-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="74017-107">Musi to być jedno, niejednoznaczne odwołanie, które nie powoduje cyklicznych odwołań między projektami.</span><span class="sxs-lookup"><span data-stu-id="74017-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="74017-108">**Identyfikator błędu:** BC30971</span><span class="sxs-lookup"><span data-stu-id="74017-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74017-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="74017-109">To correct this error</span></span>  
  
1. <span data-ttu-id="74017-110">Ustal, który projekt tworzy najlepszy zestaw dla projektu do odwołania.</span><span class="sxs-lookup"><span data-stu-id="74017-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="74017-111">W przypadku tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="74017-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="74017-112">We właściwościach projektu Dodaj odwołanie do projektu zawierającego zestaw, który definiuje używany typ.</span><span class="sxs-lookup"><span data-stu-id="74017-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74017-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74017-113">See also</span></span>

- [<span data-ttu-id="74017-114">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="74017-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="74017-115">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="74017-115">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="74017-116">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="74017-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="74017-117">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="74017-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
