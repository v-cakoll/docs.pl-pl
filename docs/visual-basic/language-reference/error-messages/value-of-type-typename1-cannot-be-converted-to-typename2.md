---
title: "Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b583c4272dd6e964de99fb14d2795152c655f3aa
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="683e6-102">Wartość typu &#39; &lt;typename1&gt;&#39; nie można przekonwertować na &#39;&lt; typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="683e6-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="683e6-103">Wartości typu "\<typename1 >' nie można przekonwertować na"\<typename2 > ".</span><span class="sxs-lookup"><span data-stu-id="683e6-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="683e6-104">Niezgodność typów przyczyną może być połączenie odwołania pliku z odwołaniem projektu do zestawu "\<assemblyname >".</span><span class="sxs-lookup"><span data-stu-id="683e6-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="683e6-105">Spróbuj zamienić odwołanie pliku do "\<ścieżka_pliku >" w projekcie "\<projectname1 >" na odwołanie projektu do "\<projectname2 >".</span><span class="sxs-lookup"><span data-stu-id="683e6-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="683e6-106">W sytuacji, gdy projekt sprawia, że zarówno odwołanie do projektu i odwołanie do pliku kompilator nie może zagwarantować, że jeden typ można przekonwertować na inny.</span><span class="sxs-lookup"><span data-stu-id="683e6-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="683e6-107">Poniższy pseudo-kod przedstawia sytuację, której może wygenerować tego błędu.</span><span class="sxs-lookup"><span data-stu-id="683e6-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="683e6-108">Projekt `P1` wykonuje odwołanie pośrednie projektu do projektu `P2` do projektu `P3`, a także bezpośrednie odwołanie do pliku `P3`.</span><span class="sxs-lookup"><span data-stu-id="683e6-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="683e6-109">Deklaracja `commonObject` używa odwołanie pliku do `P3`, podczas gdy wywołanie `P2.getCommonClass` używa odwołanie projektu do `P3`.</span><span class="sxs-lookup"><span data-stu-id="683e6-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="683e6-110">Problem w tej sytuacji jest, że odwołanie do pliku Określa ścieżkę i nazwę pliku dla pliku wyjściowego `P3` (zazwyczaj p3.dll), gdy projekt odwołuje się do identyfikacji projektu źródłowego (`P3`) według nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="683e6-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="683e6-111">W związku z tym kompilator nie może zagwarantować, że typ `P3.commonClass` pochodzi z tego samego kodu źródłowego za pomocą dwóch różnych odwołań.</span><span class="sxs-lookup"><span data-stu-id="683e6-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="683e6-112">Ta sytuacja zwykle występuje, gdy projekt odwołań i mieszane odwołania do pliku.</span><span class="sxs-lookup"><span data-stu-id="683e6-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="683e6-113">Na powyższej ilustracji, problem może nie wystąpić, jeśli `P1` wprowadzone bezpośrednie odwołanie do `P3` zamiast odwołania pliku.</span><span class="sxs-lookup"><span data-stu-id="683e6-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="683e6-114">**Identyfikator błędu:** BC30955</span><span class="sxs-lookup"><span data-stu-id="683e6-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="683e6-115">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="683e6-115">To correct this error</span></span>  
  
-   <span data-ttu-id="683e6-116">Zmień odwołanie pliku do projektu odwołanie.</span><span class="sxs-lookup"><span data-stu-id="683e6-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="683e6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="683e6-117">See Also</span></span>  
 [<span data-ttu-id="683e6-118">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="683e6-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="683e6-119">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="683e6-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
