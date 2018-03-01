---
title: Wpisz &#39; &lt;typename&gt;&#39; nie jest zdefiniowany
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="8befe-102">Wpisz &#39; &lt;typename&gt;&#39; nie jest zdefiniowany</span><span class="sxs-lookup"><span data-stu-id="8befe-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="8befe-103">Instrukcja wprowadził odwołanie do typu, który nie został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="8befe-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="8befe-104">Można zdefiniować typu w instrukcji deklaracji takich jak `Enum`, `Structure`, `Class`, lub `Interface`.</span><span class="sxs-lookup"><span data-stu-id="8befe-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="8befe-105">**Identyfikator błędu:** BC30002</span><span class="sxs-lookup"><span data-stu-id="8befe-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8befe-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8befe-106">To correct this error</span></span>  
  
-   <span data-ttu-id="8befe-107">Upewnij się, że definicji typu i jego odwołania oba rozwiązania używają tej samej pisowni.</span><span class="sxs-lookup"><span data-stu-id="8befe-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="8befe-108">Upewnij się, że definicja typu jest dostępny do odwołania.</span><span class="sxs-lookup"><span data-stu-id="8befe-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="8befe-109">Na przykład, jeśli typ znajduje się w innym module i została zadeklarowana `Private`, Przenieś definicji typu modułu odwołujący się lub Zadeklaruj `Public`.</span><span class="sxs-lookup"><span data-stu-id="8befe-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="8befe-110">Upewnij się, że obszar nazw tego typu nie zostało ponownie zdefiniowane w ramach projektu.</span><span class="sxs-lookup"><span data-stu-id="8befe-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="8befe-111">Jeśli tak jest, użyj `Global` — słowo kluczowe pełnej nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="8befe-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="8befe-112">Na przykład, jeśli projekt definiuje obszar nazw o nazwie `System`, <xref:System.Object?displayProperty=nameWithType> nie można uzyskać dostępu do typu, o ile nie jest w pełni kwalifikowanej z `Global` — słowo kluczowe: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="8befe-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="8befe-113">Jeśli typ jest zdefiniowany, ale obiekt biblioteki lub bibliotekę typów, w którym jest zdefiniowany nie jest zarejestrowany w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], kliknij przycisk **Dodaj odwołanie** na **projektu** menu, a następnie wybierz odpowiedni obiekt biblioteki lub biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="8befe-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="8befe-114">Upewnij się, że typ jest w zestawie, do którego jest częścią docelowej profilu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8befe-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="8befe-115">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z błędami docelowy Framework .NET](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="8befe-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8befe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8befe-116">See Also</span></span>  
 [<span data-ttu-id="8befe-117">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8befe-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="8befe-118">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8befe-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="8befe-119">Structure — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8befe-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="8befe-120">Class — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8befe-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="8befe-121">Interface — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8befe-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="8befe-122">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="8befe-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
