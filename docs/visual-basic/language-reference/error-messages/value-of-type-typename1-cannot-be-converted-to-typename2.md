---
title: Wartości typu „<typename1>” nie można przekonwertować na „<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: f6b35efbc445887c537b94dd299b317a28e5f689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406563"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="5f4df-102">Wartości typu „\<typename1>” nie można przekonwertować na „\<typename2>”</span><span class="sxs-lookup"><span data-stu-id="5f4df-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="5f4df-103">\<typename1>Nie można przekonwertować wartości typu "" na " \<typename2> ".</span><span class="sxs-lookup"><span data-stu-id="5f4df-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="5f4df-104">Niezgodność typów może być spowodowana mieszaniem odwołania do pliku z odwołaniem projektu do zestawu " \<assemblyname> ".</span><span class="sxs-lookup"><span data-stu-id="5f4df-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="5f4df-105">Spróbuj zastąpić odwołanie do pliku " \<filepath> " w projekcie " \<projectname1> " z odwołaniem projektu do " \<projectname2> ".</span><span class="sxs-lookup"><span data-stu-id="5f4df-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="5f4df-106">W sytuacji, gdy projekt tworzy odwołanie do projektu i odwołanie do pliku, kompilator nie może zagwarantować, że jeden typ może zostać skonwertowany na inny.</span><span class="sxs-lookup"><span data-stu-id="5f4df-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="5f4df-107">Poniższy pseudo kodu ilustruje sytuację, która może generować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="5f4df-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="5f4df-108">Program Project `P1` tworzy pośrednie odwołanie do projektu za pośrednictwem projektu `P2` do projektu `P3` , a także bezpośrednie odwołanie do pliku do `P3` .</span><span class="sxs-lookup"><span data-stu-id="5f4df-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="5f4df-109">Deklaracja `commonObject` używa odwołania pliku do `P3` , podczas gdy wywołanie `P2.getCommonClass` używa odwołania do projektu do `P3` .</span><span class="sxs-lookup"><span data-stu-id="5f4df-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="5f4df-110">Problem w tej sytuacji polega na tym, że odwołanie do pliku Określa ścieżkę i nazwę pliku wyjściowego `P3` (zazwyczaj P3. dll), podczas gdy odwołania projektu identyfikują projekt źródłowy ( `P3` ) według nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="5f4df-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="5f4df-111">W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pośrednictwem dwóch różnych odwołań.</span><span class="sxs-lookup"><span data-stu-id="5f4df-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="5f4df-112">Ta sytuacja zwykle występuje, gdy odwołania do projektu i odwołania do pliku są mieszane.</span><span class="sxs-lookup"><span data-stu-id="5f4df-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="5f4df-113">Na powyższej ilustracji problem nie wystąpi, jeśli zostanie `P1` utworzone bezpośrednie odwołanie do projektu `P3` zamiast odwołania do pliku.</span><span class="sxs-lookup"><span data-stu-id="5f4df-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="5f4df-114">**Identyfikator błędu:** BC30955</span><span class="sxs-lookup"><span data-stu-id="5f4df-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f4df-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5f4df-115">To correct this error</span></span>  
  
- <span data-ttu-id="5f4df-116">Zmień odwołanie do pliku na odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="5f4df-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4df-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f4df-117">See also</span></span>

- [<span data-ttu-id="5f4df-118">Konwersje plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f4df-118">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="5f4df-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="5f4df-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
