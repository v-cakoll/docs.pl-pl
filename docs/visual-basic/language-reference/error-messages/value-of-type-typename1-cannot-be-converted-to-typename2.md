---
title: Wartości typu „<typename1>” nie można przekonwertować na „<typename2>”
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766808"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a><span data-ttu-id="68692-102">Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >"</span><span class="sxs-lookup"><span data-stu-id="68692-102">Value of type '\<typename1>' cannot be converted to '\<typename2>'</span></span>
<span data-ttu-id="68692-103">Wartość typu "\<typename1 >" nie można przekonwertować na "\<typename2 >".</span><span class="sxs-lookup"><span data-stu-id="68692-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="68692-104">Niezgodność typów przyczyną może być połączenie odwołania pliku z odwołaniem projektu do zestawu "\<nazwa_zestawu >".</span><span class="sxs-lookup"><span data-stu-id="68692-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="68692-105">Spróbuj wymienić odwołanie pliku do "\<ścieżka_pliku >' w projekcie"\<projectname1 > "z odwołaniem projektu do"\<projectname2 > ".</span><span class="sxs-lookup"><span data-stu-id="68692-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="68692-106">W sytuacji, gdy projekt sprawia, że odwołania projektu i odwołanie do pliku kompilator nie może zagwarantować, że jeden typ może być konwertowany na inny.</span><span class="sxs-lookup"><span data-stu-id="68692-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="68692-107">Poniższy pseudo-kod pokazano sytuację, która może wygenerować tego błędu.</span><span class="sxs-lookup"><span data-stu-id="68692-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="68692-108">Projekt `P1` sprawia, że odwołanie do pośredniego projektu za pośrednictwem projektu `P2` do projektu `P3`, a także bezpośrednie odwołanie do pliku `P3`.</span><span class="sxs-lookup"><span data-stu-id="68692-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="68692-109">Deklaracja `commonObject` używa odwołanie pliku do `P3`, podczas gdy wywołaniu `P2.getCommonClass` używa odwołania projektu do `P3`.</span><span class="sxs-lookup"><span data-stu-id="68692-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="68692-110">Problem w tej sytuacji jest, że odwołanie do pliku Określa ścieżkę i nazwę pliku dla pliku danych wyjściowych `P3` (zazwyczaj p3.dll), gdy odwołania do projektu zidentyfikować projektu źródłowego (`P3`) według nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="68692-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="68692-111">W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pośrednictwem dwóch różnych odwołań.</span><span class="sxs-lookup"><span data-stu-id="68692-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="68692-112">Taka sytuacja ma zazwyczaj miejsce po projektu odwołania, a mieszane odwołania do pliku.</span><span class="sxs-lookup"><span data-stu-id="68692-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="68692-113">Na poprzedniej ilustracji, problem może nie wystąpić, jeśli `P1` wprowadzone bezpośrednie odwołanie do `P3` zamiast odwołania pliku.</span><span class="sxs-lookup"><span data-stu-id="68692-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="68692-114">**Identyfikator błędu:** BC30955</span><span class="sxs-lookup"><span data-stu-id="68692-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68692-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="68692-115">To correct this error</span></span>  
  
- <span data-ttu-id="68692-116">Zmień odwołanie do pliku z odwołaniem projektu.</span><span class="sxs-lookup"><span data-stu-id="68692-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68692-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68692-117">See also</span></span>

- [<span data-ttu-id="68692-118">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68692-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="68692-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="68692-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
