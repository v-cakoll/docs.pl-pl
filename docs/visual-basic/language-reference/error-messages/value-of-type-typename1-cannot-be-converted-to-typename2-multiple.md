---
title: Wartości typu „<typename1>” nie może zostać przekonwertowana na „<typename2>” (Odwołania do wielu plików)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833532"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="3f015-102">Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >" (odwołania do wielu plików)</span><span class="sxs-lookup"><span data-stu-id="3f015-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="3f015-103">Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >".</span><span class="sxs-lookup"><span data-stu-id="3f015-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="3f015-104">Niezgodność typów przyczyną może być połączenie odwołania pliku do "\<filepath1 >' w projekcie"\<projectname1 > "z odwołaniem do pliku"\<filepath2 >' w projekcie "\<projectname2 >".</span><span class="sxs-lookup"><span data-stu-id="3f015-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="3f015-105">Jeśli oba zestawy są identyczne, spróbuj wymienić te odwołania, tak aby oba odwołania z tej samej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3f015-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="3f015-106">W sytuacji, gdy projekt sprawia, że więcej niż jedno odwołanie pliku do zestawu kompilator nie może zagwarantować, że jeden typ może być konwertowany na inny.</span><span class="sxs-lookup"><span data-stu-id="3f015-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="3f015-107">Odwołanie do każdego pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego projektu (zwykle w pliku DLL).</span><span class="sxs-lookup"><span data-stu-id="3f015-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="3f015-108">Kompilator nie może zagwarantować, że pliki wyjściowe pochodzą z tego samego źródła lub fakt, że reprezentują tę samą wersję tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f015-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="3f015-109">W związku z tym nie gwarantuje, że typy w różne odwołania są tego samego typu lub nawet ten. mogą być konwertowane do drugiego.</span><span class="sxs-lookup"><span data-stu-id="3f015-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="3f015-110">Odwołanie do pojedynczego pliku można użyć, jeśli wiesz, że zestawy występujące w odwołaniach mają taką samą tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f015-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="3f015-111">*Tożsamości zestawu* zawiera nazwę zestawu, wersji, klucz publiczny, jeśli istnieje i kultury.</span><span class="sxs-lookup"><span data-stu-id="3f015-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="3f015-112">Te informacje w sposób unikatowy identyfikuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="3f015-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="3f015-113">**Identyfikator błędu:** BC30961</span><span class="sxs-lookup"><span data-stu-id="3f015-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f015-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3f015-114">To correct this error</span></span>  
  
-   <span data-ttu-id="3f015-115">Jeśli zestawy występujące w odwołaniach ma taką samą tożsamość zestawu, usuń lub Zamień jednego odwołania do pliku, tak, aby istniała tylko odwołanie do pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="3f015-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="3f015-116">Jeśli zestawy występujące w odwołaniach nie ma tej samej tożsamości zestawu, a następnie zmień swój kod, tak aby nie próbuje przekonwertować typu na jeden typ w innym.</span><span class="sxs-lookup"><span data-stu-id="3f015-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f015-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f015-117">See also</span></span>

- [<span data-ttu-id="3f015-118">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f015-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="3f015-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="3f015-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
