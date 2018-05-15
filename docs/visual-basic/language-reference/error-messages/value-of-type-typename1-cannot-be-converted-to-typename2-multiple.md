---
title: Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (wiele odwołań do pliku)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="4d74c-102">Wartości typu &#39; &lt;typename1&gt; &#39; nie można przekonwertować na &#39; &lt;typename2&gt; &#39; (wiele odwołań do pliku)</span><span class="sxs-lookup"><span data-stu-id="4d74c-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="4d74c-103">Wartości typu "\<typename1 >' nie można przekonwertować na"\<typename2 > ".</span><span class="sxs-lookup"><span data-stu-id="4d74c-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="4d74c-104">Niezgodność typów przyczyną może być połączenie odwołania pliku do "\<filepath1 >" w projekcie "\<projectname1 >" z odwołaniem pliku do "\<filepath2 >" w projekcie "\<projectname2 >".</span><span class="sxs-lookup"><span data-stu-id="4d74c-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="4d74c-105">Jeżeli oba zestawy są identyczne, spróbuj zamienić te odwołania, tak aby oba pochodziły z tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4d74c-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="4d74c-106">W sytuacji, gdy projekt sprawia, że więcej niż jedno odwołanie pliku do zestawu kompilator nie może zagwarantować, że jeden typ można przekonwertować na inny.</span><span class="sxs-lookup"><span data-stu-id="4d74c-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="4d74c-107">Odwołanie do każdego pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego projektu (zwykle w pliku DLL).</span><span class="sxs-lookup"><span data-stu-id="4d74c-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="4d74c-108">Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła, lub że reprezentują tej samej wersji tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d74c-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="4d74c-109">W związku z tym nie może zagwarantować, że typy w różnych odwołania są tego samego typu lub nawet co można przekonwertować na innych.</span><span class="sxs-lookup"><span data-stu-id="4d74c-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="4d74c-110">Odwołanie pojedynczego pliku można użyć, jeśli wiadomo, że zestawy występujące w odwołaniach mają tej samej tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d74c-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="4d74c-111">*Tożsamości zestawu* zawiera nazwę, wersję, klucz publiczny, jeśli istnieją i kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d74c-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="4d74c-112">Te informacje w sposób unikatowy identyfikuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d74c-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="4d74c-113">**Identyfikator błędu:** BC30961</span><span class="sxs-lookup"><span data-stu-id="4d74c-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d74c-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4d74c-114">To correct this error</span></span>  
  
-   <span data-ttu-id="4d74c-115">Jeśli zestawów występujących w odwołaniach ma taką samą tożsamość zestawu, usuń lub Zamień jedno z odwołań pliku tak, aby tylko odwołanie do pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="4d74c-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="4d74c-116">Jeśli zestawów występujących w odwołaniach nie miały tej samej tożsamości zestawu, a następnie zmień swój kod, tak aby nie próbuje przekonwertować typu w jednym z typem w innym.</span><span class="sxs-lookup"><span data-stu-id="4d74c-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d74c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d74c-117">See Also</span></span>  
 [<span data-ttu-id="4d74c-118">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d74c-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="4d74c-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="4d74c-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
