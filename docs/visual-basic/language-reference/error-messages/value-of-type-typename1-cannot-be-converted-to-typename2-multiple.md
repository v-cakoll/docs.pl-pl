---
title: Wartości typu „<typename1>” nie może zostać przekonwertowana na „<typename2>” (Odwołania do wielu plików)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 25008f05979638e050b74fc659fdc0a6d13b3c31
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406589"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="cc5c8-102">Wartości typu „\<typename1>” nie może zostać przekonwertowana na „\<typename2>” (Odwołania do wielu plików)</span><span class="sxs-lookup"><span data-stu-id="cc5c8-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="cc5c8-103">\<typename1>Nie można przekonwertować wartości typu "" na " \<typename2> ".</span><span class="sxs-lookup"><span data-stu-id="cc5c8-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="cc5c8-104">Niezgodność typów może być spowodowana mieszaniem odwołania do pliku " \<filepath1> " w projekcie " \<projectname1> " z odwołaniem do pliku " \<filepath2> " w projekcie " \<projectname2> ".</span><span class="sxs-lookup"><span data-stu-id="cc5c8-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="cc5c8-105">Jeśli oba zestawy są identyczne, spróbuj zastąpić te odwołania, aby oba odwołania były z tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="cc5c8-106">W sytuacji, gdy projekt składa więcej niż jedno odwołanie do zestawu, kompilator nie może zagwarantować, że jeden typ może być konwertowany na inny.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="cc5c8-107">Każde odwołanie do pliku Określa ścieżkę i nazwę pliku wyjściowego projektu (zazwyczaj jest to plik DLL).</span><span class="sxs-lookup"><span data-stu-id="cc5c8-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="cc5c8-108">Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła lub reprezentują te same wersje tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="cc5c8-109">W związku z tym nie może zagwarantować, że typy w różnych odwołaniach są tego samego typu, lub nawet że jeden z nich można przekonwertować na drugi.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="cc5c8-110">Można użyć jednego odwołania do pliku, Jeśli wiesz, że zestawy, do których istnieją odwołania, mają tę samą tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="cc5c8-111">*Tożsamość zestawu* zawiera nazwę zestawu, wersję, klucz publiczny, jeśli istnieje, oraz kulturę.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="cc5c8-112">Te informacje jednoznacznie identyfikują zestaw.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="cc5c8-113">**Identyfikator błędu:** BC30961</span><span class="sxs-lookup"><span data-stu-id="cc5c8-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc5c8-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cc5c8-114">To correct this error</span></span>  
  
- <span data-ttu-id="cc5c8-115">Jeśli zestawy, do których się odwołuje, mają tę samą tożsamość zestawu, Usuń lub Zastąp jedno z odwołań do pliku, tak że istnieje tylko jedno odwołanie do pliku.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
- <span data-ttu-id="cc5c8-116">Jeśli zestawy, do których się odwoływano, nie mają tej samej tożsamości zestawu, a następnie Zmień kod, tak aby nie próbował skonwertować typu w jeden do typu w drugim.</span><span class="sxs-lookup"><span data-stu-id="cc5c8-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5c8-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc5c8-117">See also</span></span>

- [<span data-ttu-id="cc5c8-118">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc5c8-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="cc5c8-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="cc5c8-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
