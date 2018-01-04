---
title: "Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39; (Wiele odwołań do pliku)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f22516a5ca9626f43cb89745e67c66619cf9461f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="9c8b5-102">Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39; (Wiele odwołań do pliku)</span><span class="sxs-lookup"><span data-stu-id="9c8b5-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="9c8b5-103">Wartości typu "\<typename1 >' nie można przekonwertować na"\<typename2 > ".</span><span class="sxs-lookup"><span data-stu-id="9c8b5-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="9c8b5-104">Niezgodność typów przyczyną może być połączenie odwołania pliku do "\<filepath1 >" w projekcie "\<projectname1 >" z odwołaniem pliku do "\<filepath2 >" w projekcie "\<projectname2 >".</span><span class="sxs-lookup"><span data-stu-id="9c8b5-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="9c8b5-105">Jeżeli oba zestawy są identyczne, spróbuj zamienić te odwołania, tak aby oba pochodziły z tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="9c8b5-106">W sytuacji, gdy projekt sprawia, że więcej niż jedno odwołanie pliku do zestawu kompilator nie może zagwarantować, że jeden typ można przekonwertować na inny.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="9c8b5-107">Odwołanie do każdego pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego projektu (zwykle w pliku DLL).</span><span class="sxs-lookup"><span data-stu-id="9c8b5-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="9c8b5-108">Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła, lub że reprezentują tej samej wersji tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="9c8b5-109">W związku z tym nie może zagwarantować, że typy w różnych odwołania są tego samego typu lub nawet co można przekonwertować na innych.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="9c8b5-110">Odwołanie pojedynczego pliku można użyć, jeśli wiadomo, że zestawy występujące w odwołaniach mają tej samej tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="9c8b5-111">*Tożsamości zestawu* zawiera nazwę, wersję, klucz publiczny, jeśli istnieją i kultury zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="9c8b5-112">Te informacje w sposób unikatowy identyfikuje zestawu.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="9c8b5-113">**Identyfikator błędu:** BC30961</span><span class="sxs-lookup"><span data-stu-id="9c8b5-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c8b5-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9c8b5-114">To correct this error</span></span>  
  
-   <span data-ttu-id="9c8b5-115">Jeśli zestawów występujących w odwołaniach ma taką samą tożsamość zestawu, usuń lub Zamień jedno z odwołań pliku tak, aby tylko odwołanie do pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="9c8b5-116">Jeśli zestawów występujących w odwołaniach nie miały tej samej tożsamości zestawu, a następnie zmień swój kod, tak aby nie próbuje przekonwertować typu w jednym z typem w innym.</span><span class="sxs-lookup"><span data-stu-id="9c8b5-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8b5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c8b5-117">See Also</span></span>  
 [<span data-ttu-id="9c8b5-118">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c8b5-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="9c8b5-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="9c8b5-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
